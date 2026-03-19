# IMMERSE | SMART FOCUS DESK  

https://wokwi.com/projects/448282317388981249

### Global Solution – EDGE Computing (FIAP)

## 👥 Integrantes
- **Fábio Alexandre Barbosa Filho – RM: 567419**  

---

## 🚀 Descrição do Projeto
O **Smart Focus Desk** integra-se ao ecossistema da plataforma **IMMERSE**, auxiliando no monitoramento de temperatura e umidade do ambiente de trabalho.  
Com base nesses dados, o sistema identifica condições ambientais desfavoráveis e alerta o usuário através de um LED indicativo.

---

## 🎯 Objetivo
- Monitorar o ambiente de trabalho.  
- Detectar condições de desconforto térmico.  
- Alertar o usuário quando a produtividade pode ser prejudicada.  
- Demonstrar o papel de sistemas embarcados no Futuro do Trabalho.

---

## 🧠 Como Funciona
- O **DHT22** coleta temperatura e umidade.  
- O Arduino analisa os valores.  
- Se **Temperatura > 30°C** ou **Umidade < 35%**, o LED acende.  
- Caso contrário, o LED permanece apagado.

### Lógica:
```
if (temperatura > 30°C OR umidade < 35%) {
    LED = ON;
} else {
    LED = OFF;
}
```

---

## 🔧 Componentes Utilizados
- Arduino UNO  
- Sensor DHT22  
- LED vermelho  
- Resistor de 220 Ω  
- Jumpers  
- Botão (opcional)

---

## 🛠 Esquema de Conexão

### DHT22  
| Pino | Ligação |
|------|---------|
| VCC | 5V |
| DATA | D2 |
| NC | — |
| GND | GND |

### LED  
- Anodo → Resistor → D3  
- Catodo → GND  

---

## 📂 Código Utilizado
```cpp
#include <DHT.h>

#define DHTPIN   2
#define DHTTYPE  DHT22
#define LEDPIN   3

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
  pinMode(LEDPIN, OUTPUT);
  digitalWrite(LEDPIN, LOW);
}

void loop() {
  float t = dht.readTemperature();
  float h = dht.readHumidity();

  Serial.print("Temp: ");
  Serial.print(t);
  Serial.print("  | Umid: ");
  Serial.println(h);

  bool risco = false;

  if (!isnan(t) && t > 30) risco = true;
  if (!isnan(h) && h < 35) risco = true;

  if (risco) digitalWrite(LEDPIN, HIGH);
  else digitalWrite(LEDPIN, LOW);

  delay(1000);
}
```

---

## 🧪 Demonstração
- LED apagado: ambiente normal  
- LED aceso: ambiente desconfortável  

---

## 🚧 Dificuldades
- Ajuste de leitura do DHT22  
- Estabilidade do sensor  
- Correção da lógica de risco

---

## ⭐ Diferenciais
- Baixo custo  
- Alta aplicabilidade  
- Simples e funcional  
- Relacionado diretamente ao Futuro do Trabalho

---

## 📎 Licença
Uso educacional para Global Solution – FIAP.
