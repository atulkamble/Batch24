# Batch24
Codes and Notes

### Webseerver script
```
#!/bin/bash
echo "installing apache"
sudo apt update
sudo apt install apache2 -y 
echo "starting apache service"
sudo systemctl start apache2
sudo systemctl enable apache2 
cd /var/www/html 
sudo chmod 755 /var/www/html 
sudo rm index.html
sudo touch index.html 
echo "<h1>Webserver</h1>" | sudo tee /var/www/html/index.html > /dev/null
echo "Done!"
```
