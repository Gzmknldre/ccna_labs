# 36 - Quality of Service (QoS)

## 🔹 QoS Nedir?

**QoS (Quality of Service)**, ağ trafiğini belirli kriterlere göre sınıflandırıp önceliklendirerek önemli trafiğin daha iyi hizmet almasını sağlar.

QoS özellikle **bandwidth, delay, jitter ve packet loss** gibi problemlerin yönetilmesinde kullanılır.

---

## 🔹 PoE (Power over Ethernet)

**PoE**, Ethernet kablosu üzerinden hem **data hem de güç** taşınmasını sağlar.

Örneğin:
- IP Phone
- Access Point
- IP Camera

aynı Ethernet bağlantısından güç alabilir.

---

## 🔹 Queuing

**Queuing**, paketlerin gönderilmeden önce kuyruklarda bekletilmesi ve hangi paketin önce gönderileceğinin belirlenmesidir.

Trafik yoğun olduğunda QoS, önemli paketlere öncelik verilmesini sağlar.

Temel amaç:

> Önemli trafik → daha yüksek öncelik  
> Daha az önemli trafik → daha düşük öncelik

---

## 🔹 Classification

**Classification**, ağ trafiğini belirli özelliklerine göre sınıflandırma işlemidir.

Paketler örneğin:
- IP adresi
- Protocol
- Port
- QoS marking

gibi bilgiler kullanılarak farklı sınıflara ayrılabilir.

Classification → **Trafiğin hangi sınıfa ait olduğunu belirler.**

---

## 🔹 PCP

**PCP (Priority Code Point)**, Ethernet frame içindeki **802.1Q VLAN tag** içerisinde bulunur.

- **3 bit**
- **0–7** arasında değer alır
- Layer 2 seviyesinde öncelik belirtir.

| PCP | Priority |
|---|---|
| 0 | Best Effort |
| 1 | Background |
| 2 | Spare |
| 3 | Excellent Effort |
| 4 | Controlled Load |
| 5 | Video |
| 6 | Voice |
| 7 | Network Control |

**PCP → Layer 2 marking**

---

## 🔹 DSCP

**DSCP (Differentiated Services Code Point)**, IP header içerisindeki **6 bitlik** alandır.

Trafiğin QoS açısından nasıl ele alınacağını belirtmek için kullanılır.

### DF – Default Forwarding

**DF (Default Forwarding)**, normal / best-effort trafik için kullanılır.

- Özel bir öncelik verilmez.
- Normal trafik olarak iletilir.

### EF – Expedited Forwarding

**EF (Expedited Forwarding)**, düşük delay ve düşük jitter gerektiren trafik için kullanılır.

Örneğin **voice traffic** için uygundur.

**EF → DSCP 46**

> PCP → Layer 2  
> DSCP → Layer 3

---

## 🔹 RED

**RED (Random Early Detection)**, congestion oluşmadan önce bazı paketleri rastgele drop ederek congestion'ı önlemeye çalışır.

Kuyruk dolmaya başladığında paketlerin drop edilme ihtimali artar.

Amaç:

**Congestion başlamadan önce queue'nun kontrol altında tutulması.**

---

## 🔹 WRED

**WRED (Weighted Random Early Detection)**, RED'in geliştirilmiş halidir.

Paketlerin **priority / marking değerlerini** dikkate alarak farklı trafik türlerine farklı drop olasılıkları uygulayabilir.

Daha düşük öncelikli paketler daha erken drop edilebilirken, daha önemli trafik korunabilir.

> RED → genel random early drop  
> WRED → trafik önceliğini dikkate alarak early drop

---

## 🔹 CBWFQ

**CBWFQ (Class-Based Weighted Fair Queuing)**, trafiği sınıflara ayırarak her sınıfa belirli miktarda bandwidth tahsis edilmesini sağlar.

- Trafik sınıflandırılır.
- Her class için bandwidth belirlenebilir.
- Class'lar kendi queue'larında işlenir.

Örneğin:

```text
Voice       → %30
Video       → %40
Data        → %30
