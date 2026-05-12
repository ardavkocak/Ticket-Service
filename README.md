# Bilet Rezervasyon Sistemi

Java Swing tabanlı bir **çok modlu ulaşım bilet rezervasyon sistemi** taslağı. Otobüs, tren ve uçak için sefer/rota tanımlama, koltuk seçimi ile rezervasyon ve şirket bazlı kâr hesaplama mantığı modellenmiştir. Nesne yönelimli tasarım prensipleri (kalıtım, polimorfizm, arayüzler) üzerine kurgulanmıştır.

## Özellikler

- **Çok modlu ulaşım**: Otobüs (`Bus`), Tren (`Train`), Uçak (`Airplane`) — hepsi `Vehicle` soyut sınıfından türetilmiştir
- **Kullanıcı rolleri**: `Customer`, `Admin`, `Personel`, `Passenger` (hepsi `Person`/`User` üzerinden)
- **Rezervasyon**: yolcu + araç + koltuk üçlüsü ile bilet rezervasyonu
- **Sefer/Rota yönetimi**: `Route` (kalkış–varış), `Trip` (güzergâh, zaman, fiyat)
- **Şirket modeli**: `Company` — `IProfitable` arayüzü ile kâr hesabı
- **Java Swing UI**: rezervasyon, sefer seçimi, koltuk seçimi için pencereler

## Mimari (OOP Yapısı)

```
Person
 ├── User (ILoginable)
 │    ├── Customer
 │    ├── Admin
 │    └── Personel
 └── Passenger

Vehicle (abstract)
 ├── Bus
 ├── Train
 └── Airplane

Transport  → IReservable
Company    → IProfitable

Reservation  ─→ Passenger + Vehicle + Seat
Trip / Route → güzergâh, zaman, fiyat
```

### Arayüzler
| Arayüz | Sorumluluk |
|--------|------------|
| `ILoginable` | Giriş yapabilen varlıklar (User) |
| `IReservable` | Rezervasyon yapılabilen taşıma seçenekleri (Transport) |
| `IProfitable` | Kâr/zarar hesabı yapabilen varlıklar (Company) |

## Çalıştırma

NetBeans veya IntelliJ IDEA içinde projeyi açın:

```bash
javac -d out src/projetaslak/*.java
java -cp out projetaslak.Main
```

## Dosya Yapısı

```
src/projetaslak/
├── Main.java            # Swing UI giriş noktası
├── Person.java, User.java, Customer.java, Admin.java, Personel.java, Passenger.java
├── Vehicle.java         # abstract
├── Bus.java, Train.java, Airplane.java
├── Transport.java
├── Route.java, Trip.java
├── Seat.java
├── Reservation.java
├── Company.java
├── ILoginable.java, IReservable.java, IProfitable.java
└── ../Takvim.txt        # Geliştirme takvimi/notları
```

## Bağlam

Nesneye Yönelik Programlama dersi kapsamında geliştirilmiş, OOP tasarım prensipleri (kalıtım, abstract sınıf, çoklu arayüz uygulaması) için bir proje taslağı.
