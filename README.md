# gitlab.runner.inistall
## Install runner
### 1. Simply download one of the binaries for your system:
```shell
sudo curl -L --output /usr/local/bin/gitlab-runner "https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64"
```
### 2. Give it permissions to execute:
```shell
sudo chmod +x /usr/local/bin/gitlab-runner
```
### 3. Create a GitLab CI user:
```shell
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash
```
### 4. Install and run as service:
```js
sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
sudo gitlab-runner start
```
### 5. Register executor
```shell
sudo gitlab-runner register -n \
  --url https://gitlab.com/ \
  --registration-token $TOKEN \
  --executor docker \
  --description "crm-backend-runner" \
  --docker-image "alpine:latest" \
  --docker-privileged \
  --docker-volumes "/certs/client"
  --run-untagged="true" \
  --locked="false" \
  --access-level="not_protected"`
```  
  
### Verify executor
sudo gitlab-runner verify


## Eslatma:
Yuqorida biz yaratganimizdek, ismi " gitlab-runner " bo'lgan foydalanuvchi sizning serveringizda buyruqni bajarish uchun ruxsatga ega bo'lishi kerak.

Biz NOPASSWD bilan foydalanuvchiga ruxsat berishimiz kerak, chunki quvur liniyasi ishga tushganda u parolni so'ramaydi.

## Sudoers faylingizni tahrirlang
```shell
vi /etc/sudoers
```
Quyidagi buyruq yordamida GitLab runnerini ishga tushiring

```shell
sudo gitlab-runner start
```
Endi siz yuguruvchining holatini tekshirishingiz mumkin
```shell
service gitlab-runner status
```
## Endi Gitlab-da omborni yarating
```shell
image.png
```
Yuguruvchingizni serveringizda sozlang va ro'yxatdan o'tkazing

Yuguruvchingizni sozlash uchun GitLab-ni oching va joylashtirishni o'rnatmoqchi bo'lgan omborni oching.

Loyiha sozlamalari > CI/CD-ga o'ting va yuguruvchi bo'limini kengaytiring.

Siz quyida ma'lumotni, GitLab misol URL  va  tokenni ko'rasiz

## Endi Ubuntu Serveringizda Quyidagi Buyruqni Ishga Tushiring

```shell
sudo gitlab-runner register
```
## Bu quyidagi qadamlar bilan qisqa konfiguratsiyani boshlaydi:

```shell
GitLab namunasi URL-manzilini kiriting (masalan,  https://gitlab.com/)  - URLni GitLab-da ko'rsatilgandek nusxalash va joylashtirish kifoya.

*Ro'yxatdan o'tish tokenini kiriting - Ro'yxatdan o'tish tokenini GitLab-da ko'rsatilgandek nusxa ko'chiring va joylashtiring.

*Yuguruvchi uchun tavsifni kiriting — Standart nomdan foydalanish uchun Enter/Return tugmasini bosish kifoya.

*Yuguruvchi uchun teglarni kiriting (vergul bilan ajratilgan) — Buni hozircha boʻsh qoldirishingiz mumkin. Buni keyinroq GitLab'dan o'zgartirishingiz mumkin . Davom etish uchun Enter va Return tugmalarini bosing.

*Yuguruvchi uchun ixtiyoriy texnik eslatmani kiriting - Buni bo'sh qoldirishingiz mumkin.

*Ijrochini kiriting: custom, docker, ssh, VirtualBox, docker-ssh+machine, Kubernetes, docker-ssh, parallels, shell, docker+machine —
Agar siz Docker-ni o'rnatgan bo'lsangiz,  docker ijrochini belgilashingiz mumkin.

*Standart Docker tasvirini kiriting (masalan, ruby:2.7) — Davom etish uchun siz standartdan foydalanishingiz va Enter/Return tugmasini bosishingiz mumkin.

```
