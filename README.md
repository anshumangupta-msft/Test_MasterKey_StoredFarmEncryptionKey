# Test_MasterKey_StoredFarmEncryptionKey

SharePoint keeps RegistryPassphraseKey/Masterkey on each server in farm at HKLM\SOFTWARE\Microsoft\Shared Tools\Web Server Extensions\16.0\Secure\FarmAdmin\CredentialKeyDPEnt which is unique on each server due to the local encryption used using DPAPI with machine keys of local SharePoint server.

For many significant operations(For eg add new server to farm), it will use combination of RegistryPassphraseKey/Masterkey and StoredFarmEncryptionKey and calls internal method DecryptWithRegistryPassphraseKey. If RegistryPassphraseKey/Masterkey and StoredFarmEncryptionKey are not right, the decyption fails and the operation also fails with erorr in ULS/UI like "Error during decryption. System error code 0." or "Decryption failed with error: 0" . Below script simulates the same internal calls and gives a way to test  RegistryPassphraseKey/Masterkey on server and StoredFarmEncryptionKey's health. 
