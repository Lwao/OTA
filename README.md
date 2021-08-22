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


- Situação atual:

ge42_1.2.2.spiffs.bin              -> busca -> ge42_1.2.3.spiffs.bin 
ge42_firmware_1.2.2.ino.esp32.bin  -> busca -> ge42_firmware_1.2.3.ino.esp32.bin

- Situação H4CK:

Disponibiliza apenas o Sketch: ge42_firmware_1.2.3.ino.esp32.bin, porém com o ge alterado internamente (ge8000)

- Situação atualizada temporariamente:

Apesar de não ser encontrado ge8000.txt/ge42.txt no sistema, caso não haja re-início, as credenciais da rede se manterão, fazendo com que:

                                     -> busca -> ge8000_1.2.4.spiffs.bin 
ge8000_firmware_1.2.3.ino.esp32.bin  -> busca -> ge8000_firmware_1.2.4.ino.esp32.bin

Neste caso oferece-se apenas a atualização para o spiffs e ge8000_1.2.4.spiffs.bin será interpretado como ge8000_1.2.3.spiffs.bin, já que a importância de suas versão se dá apenas com a alteração do binário 

- Situação atualizada estável:

ge8000_1.2.3.spiffs.bin              -> busca -> ge8000_1.2.4.spiffs.bin 
ge8000_firmware_1.2.3.ino.esp32.bin  -> busca -> ge8000_firmware_1.2.4.ino.esp32.bin

### Algoritmo:
- Versão atual ge42_1.2.2;
- Sketch da próxima versão como ge42_1.2.3 com o ge8000 internamente;
- Spiffs da próxima versão como ge8000_1.2.4;