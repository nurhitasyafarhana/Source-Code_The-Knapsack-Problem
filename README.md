def knapsack_dp(kapasitas, berat_barang, keuntungan, jumlah_barang):
    # Inisialisasi tabel DP dengan 0
    dp = [[0 for _ in range(kapasitas + 1)] for _ in range(jumlah_barang + 1)]

    # Proses DP untuk mencari keuntungan maksimum
    for i in range(1, jumlah_barang + 1):
        for k in range(kapasitas + 1):
            if berat_barang[i - 1] <= k:
                dp[i][k] = max(keuntungan[i - 1] + dp[i - 1][k - berat_barang[i - 1]], dp[i - 1][k])
            else:
                dp[i][k] = dp[i - 1][k]

    return dp[jumlah_barang][kapasitas]

# Input data
tingkat_keuntungan = list(map(int, input("Masukkan keuntungan barang (dalam Rp): ").split()))
bobot_barang = list(map(int, input("Masukkan berat barang (dalam kg): ").split()))
kapasitas_maksimum = int(input("Masukkan kapasitas maksimum knapsack (dalam kg): "))

jumlah_barang = len(bobot_barang)

# Output hasil
hasil_keuntungan = knapsack_dp(kapasitas_maksimum, bobot_barang, tingkat_keuntungan, jumlah_barang)
print(f"Keuntungan maksimum yang bisa diperoleh: Rp{hasil_keuntungan}")
