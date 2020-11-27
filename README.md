
# CloudBerry - Gettting Started Guide

[![Build Status](https://travis-ci.com/olliekrk/cloud-berry.svg?token=Ud4LPsJ6sjn1qVy7MUNS&branch=master)](https://travis-ci.com/olliekrk/cloud-berry)
[![HitCount](http://hits.dwyl.com/olliekrk/cloud-berry.svg)](http://hits.dwyl.com/cloudberry-agh-team/cloudberry-getting-started)
[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

---

(PL)

## Spis treści

- [Wymagania wstępne](#requirements)
- [Korzystanie z systemu](#usage)
- [Team](#team)
- [Licencja](#license)
- [Obrazy DockerHub](#dockerhub)

---

## Wymagania wstępne

- JRE 15
- Docker and docker-compose
- Python 3.8 for notebooks

Należy upewnić się, że następujące porty sieciowe są lokalnie dostępne:
* 9000 TCP - dla aplikacji serwerowej cloudberry-cb
* 90 TCP - dla aplikacji internetowej cloudberry-ng
* 9999 TCP - dla bazy danych InfluxDB
* 27017 TCP - dla bazy danych MongoDB
* 2181 TCP - dla usługi Zookeeper
* 9092 TCP - dla usługi Kafka
* 8125 UDP (opcjonalnie) - dla usługi Telegraf
* 8888 TCP (opcjonalnie) - dla usługi Jupyter Notebook

### Konfiguracja aplikacji w trybie produkcyjnym

#### Uruchomienie systemu

Aby uruchomić system z poziomu katalogu `docker` należy wykonać poniższe akcje:

* Korzystamy z jednego pliku konfiguracyjnego `app-prod.yml`, i uruchamiamy go poleceniem 
`docker-compose -f app-prod.yml up -d`.
* Należy następnie upewnić się, czy Docker uruchomił wszystkie kontenery.
* Przy pierwszym uruchomieniu, w kontenerze `influxdb-cb` należy uruchomić polecenie ze skryptu `influx-setup.sh`, znajdujcego się w folderze `docker/scripts`, które odpowiednio zainicjuje bazę danych - utworzy domyślne konto oraz
 tokeny dostępu. Można to zrobić przy pomocy `docker exec -it influxdb-cb -- /bin/bash` i następnie uruchamiając w kontenerze komendę z powyższego pliku.
* Celem weryfikacji, można sprawdzić czy interfejs bazy InfluxDB jest dostępny pod adresem `http://localhost:9999`. W domyślnej konfiguracji nazwa użytkownika to `root` a hasło `ziemniak`. Logowanie powinno zakończyć się z powodzeniem.

#### Weryfikacja

Po uruchomieniu, w domyślnej konfiguracji z pliku `app-prod.yml`, aplikacje będą dostępne pod adresami:
* http://localhost:90/ - aplikacja internetowa `cloudberry-ng` (frontend)
* http://localhost:9000/ - aplikacja serwerowa `cloudberry-cb` (backend)

Dodatkowo
* http://localhost:9999/ - interfejs graficzny bazy danych InfluxDB.
* http://localhost:9000/swagger-ui - dokumentacja REST API aplikacji serwerowej

---

## Korzystanie z systemu

* Demonstracyjne przykłady użycia aplikacji zwarte w plikach Jupyter Notebook znajdują się w katalogu `cloudberry-py`. Przed użyciem biblioteki Python należy zainstalować niezbędne biblioteki z poziomu tego katalogu wywołując `python3 -m pip install -r requirements.txt`.
* Przykładowe dane akceptowane przez bibliotekę są dostępne w folderze `cloudberry-py/data`.
* Kod biblioteki znajduje się w `cloudberry-py/cloudberry`.

---

## Team

| <a href="http://github.com/mimagiera" target="_blank">**Michał Magiera**</a> | <a href="http://github.com/olliekrk" target="_blank">**Olgierd Królik**</a> |
| :---: |:---:|
| [![mimagiera](https://avatars0.githubusercontent.com/u/43969709?s=200&v=4)](http://github.com/mimagiera)    | [![olliekrk](https://avatars3.githubusercontent.com/u/37264550?s=200&u=40b1359dfb778fe2ca75f57ed4e62acc203940a1&v=4)](http://github.com/olliekrk) |
| <a href="http://github.com/mimagiera" target="_blank">`github.com/mimagiera`</a> | <a href="http://github.com/olliekrk" target="_blank">`github.com/olliekrk`</a> |

---

## Licencja

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

- **[MIT license](http://opensource.org/licenses/mit-license.php)**


---

## Obrazy aplikacji cloudberry w DockerHub:
- **[cloudberry](https://hub.docker.com/repository/docker/olliekrk/cloudberry)**
- **[cloudberry-ng](https://hub.docker.com/repository/docker/olliekrk/cloudberry-ng)**
