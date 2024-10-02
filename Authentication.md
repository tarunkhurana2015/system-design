# Design flow for user authentocation using Apple's biometrics and your backend 

+-------------------+                       +-------------------------+
|   iOS Application  |                       |  Backend Server         |
+-------------------+                       +-------------------------+
         |                                            |
         |<----- User enters credentials -------------|    
         |                                            |
         |----- Sends credentials over HTTPS -------->|  
         |                                            |
         |<--- Server verifies & returns token -------|  
         |                                            |
         | Store token (JWT/Session Token) in Keychain|
         |                                            |
         |-- Prompt user to enable biometrics (LA API)| 
         |                                            |
         |  Future Login: Biometric Auth Success      |
         |                                            |
         | Retrieve token from Keychain               |
         |                                            |
         |----- Send token to backend for validation ->|
         |                                            |
         |<-- Server verifies token & grants access --|
         |                                            |
         +--------------------------------------------+
