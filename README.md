# Volara
Bu rehber, Volara projesi için bir miner kurulumu yaparken izlenecek adımları içermektedir. Screen komutları ile çalışmaya uygun şekilde hazırlanmıştır.

# Ön Hazırlık Aşaması

- Ubuntu 20.04 veya üstü bir Linux sunucu. Ben hem Volara hem de SixGPT aynı sunucuda çalıştırıyorum, sunucu Hetzner CX32.
- Twitter ve Gmail hesabı bağlamanız gerekmekte. Bu nedenle ben yeni bir Twitter hesabı açtım, birkaç hesap takip ettim, ortalama 50 civarında. Normal hesaplarda günlük sınırlama olduğu için de Twitter Blue aldım hesabıma sorunsuz veri işlemesi için. Bununla birlikte yeni bir Gmail hesabı açtım burada kullanmak için.
- Vana cüzdanı oluşturun ya da mevcut Vana cüzdanınıza minimum 0.1 $VANA atın. (Ben 0.5 $VANA attım, uzunca süre yetecektir.)
- https://volara.xyz/ sitesine giderek Twitter hesabınızı bağlayın. Gerekli onayı verdikten sonra Validate tuşuna basarak işlemi onaylayın. **Not: Bunu yapmadan önce Vana Mainnet ağını Metamask'a eklemeniz gerekiyor, bunun için https://chainlist.org/ kullanabilirsiniz.**

**Not: Eğer SixGPT ile birlikte kuruyorsanız direk 4. Aşamadan başlayın. Aksi halde 1. aşamadan başlayarak kurulumu gerçekleştireceksiniz.**

# Kurulum Kodları

**1. Sunucuyu Güncelleyin**

```bash
sudo apt update && sudo apt upgrade -y 
```

**2. Gerekli Paketleri Yükleyin**

```bash
sudo apt install curl wget git screen build-essential -y
```

**3. Docker Kurulumunu Gerçekleştirin**

Ubuntu sunucunuza Docker ve Docker Compose kurulumu için gerekli komutları paylaşıyorum:

1. Önce eski Docker sürümlerini kaldıralım (eğer varsa):
```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

2. Gerekli paketleri yükleyelim:
```bash
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release
```

3. Docker'ın GPG anahtarını ekleyelim:
```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

4. Docker repository'sini ekleyelim:
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Docker Engine'i yükleyelim:
```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

6. Docker Compose'u yükleyelim:
```bash
sudo apt-get update
sudo apt-get install docker-compose-plugin
```

7. Docker'ın düzgün çalıştığını kontrol edelim:
```bash
sudo docker run hello-world
```

8. (Opsiyonel) Docker'ı sudo olmadan kullanabilmek için kullanıcınızı docker grubuna ekleyin:
```bash
sudo usermod -aG docker $USER
```
Bu komutu çalıştırdıktan sonra oturumu kapatıp tekrar açmanız gerekecektir.

9. Docker ve Docker Compose versiyonlarını kontrol edebilirsiniz:
```bash
docker --version
docker compose version
```

Bu komutları sırasıyla çalıştırdığınızda Docker ve Docker Compose sisteminize kurulmuş olacaktır. Herhangi bir sorunla karşılaşırsanız belirtebilirsiniz.

**4. Arka Planda Çalıştırmak İçin Screen Açın**

Screen komutu ile işlemleri arka planda yürütebilmek için yeni bir oturum başlatın:
```bash
screen -S volara
```

**5. Volara Miner Kurulumunu Gerçekleştirin**
```bash
[ -f "volara.sh" ] && rm volara.sh; curl -s -o volara.sh https://raw.githubusercontent.com/volaradlp/minercli/refs/heads/main/run_docker.sh && chmod +x volara.sh && ./volara.sh
```

Bu aşamadan sonra Volara Miner çalışmaya başlayacak.

**6. Volara Miner İçin Gerekli Hesapları Bağlayın**

Enter your burner wallet's private key: <Buraya Kullanacağınız Cüzdanınızın Private Key'ini yapıştırıp ENTER basın.





