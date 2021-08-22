# OTA

esp32 update via over-the-air programming

Preocupações: mudar version do sketch OTA do 1.0.X para 1.0.X+1 (dois cantos)
Padrão ID do dispositivo
Alterar version no efetuarLeitura() versão 1.0
Localiza o .pio\buld\lolin32\firmware.bin
Jogar o .bin no repositório e alterar o nome para a nova versão (cuidado para manter a versão anteriormente inserida)

Data:

altera ge120.txt
e roda a task Upload Filesystem Image
Localiza o .pio\buld\lolin32\spiffs.bin
Põe no repositório


### Parâmetros do teste

- Atualizações em intervalos de 1min;
- A versão atual busca a próxima versão do mesmo sensor (atualizar versão);
- A versão atual busca a mesma versão de outro sensor (atualizar sensor);
- Deve-se atualizar o sketch e o spiffs;


ge42_1.2.2.spiffs.bin
ge_firmware_1.2.2.ino.esp32.bin