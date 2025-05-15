# IoT25-HW7
Assignment of IoT HW

BLE-Based Distance Estimation

Environment: Indoor corridor (minimal obstacles), temperature ≈ 22 °C

Hardware:

ESP32 BLE Server broadcasting at txPower = –59 dBm (measured at 1 m)

ESP32 BLE Client scanning and recording RSSI

Path-loss model: ![image](https://github.com/user-attachments/assets/8d613db9-2c39-45b5-89eb-a8d61ea2ce51)


Procedure:

Place Server and Client at a fixed separation (0.5 m, 1 m, 2 m, 3 m, 4 m).

At each distance, record 10 RSSI samples on the Client.

Compute estimated distance for each sample via estimateDistance(rssi).

Calculate the mean estimated distance at each true distance.

Summary Table True Distance (m) Mean Estimated (m) Error (m) Error Rate (%) 0.5 0.47 0.03 6.0 1.0 1.12 0.12 12.0 2.0 2.05 0.05 2.5 3.0 3.30 0.30 10.0 4.0 3.90 0.10 2.5

bar chart
![image](https://github.com/user-attachments/assets/5feac092-bdc9-4b2a-a63b-5b0d53f9baa9)
At distances of 2 m and 4 m, the BLE-based estimator achieved its best accuracy, with error rates as low as 2.5 %, whereas at 1 m and 3 m the deviations were larger—up to 10–12 %. Such variations are largely attributable to environmental factors: in our indoor corridor setting, multipath reflections cause the RSSI to fluctuate, and occasional human movement or slight changes in device orientation introduce additional noise. To improve overall performance, we recommend applying a moving-average filter to smooth out rapid RSSI spikes and, for even greater stability, incorporating a Kalman filter to dynamically correct measurement noise. Finally, gathering extra calibration data at intermediate points (for example at 1.5 m and 2.5 m) will allow you to refine both the txPower reference and the path-loss exponent n, further reducing systematic bias.

# HW07_1 : Server Code
![스크린샷 2025-05-15 033510](https://github.com/user-attachments/assets/1130fc02-8549-4824-b569-27ff4d994cf1)

# HW07_2 : Client Code
![스크린샷 2025-05-15 033525](https://github.com/user-attachments/assets/b0f3b832-5d8f-43a7-858d-9630111cac5a)

# HW07_2_1 : Bouns 1 add
![스크린샷 2025-05-15 060145](https://github.com/user-attachments/assets/99d43411-94e9-4672-9fdc-5a6108c0fe0a)
![KakaoTalk_20250515_060257335](https://github.com/user-attachments/assets/20b22df7-9823-4929-b7e1-4a39040b48b3)

# HW07_2_2 : Bonus 2 add
![KakaoTalk_20250515_045954056](https://github.com/user-attachments/assets/c70101f9-82a2-4585-ae1a-b6b4593554d7)
