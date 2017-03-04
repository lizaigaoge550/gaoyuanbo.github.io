###运行出现java.lang.NoSuchDefClass:scala$product,这是因为scala版本没有整对，换成2.10.5
###出现javax.servlet错误，可能是servlet包冲突
###java.lang.SecurityException: Invalid signature file digest for Manifest main attributes 方法：zip -d your.jar 'META-INF/.SF' 'META-INF/.RSA' 'META-INF/*SF'
