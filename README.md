# neo-tex-env

Środowisko Dockerowe do budowania śpiewnika i innych materiałów Drogi Neokatechumenalnej
dostępnych na http://spiewnik.andrzej.odyniec.info

## Pobieranie zbudowanego kontenera

```
docker pull ghcr.io/michals/neo-tex-env:tl2018-fonts
```

## Uruchomienie kontenera

```
docker run -it --rm -v /full/path/to/tex/files/:/mnt ghcr.io/michals/neo-tex-env:tl2018-fonts
# potem już w kontenerze, np:
lualatex /mnt/ReadMe.tex
```

## Pobranie z kontenera zbudowanego dokumentu:
```
# UWAGA: Jeśli kontener był uruchomiony z opcją `--rm` to trzeba to zrobić w drugim oknie terminala póki kontener jeszcze działa
docker cp $(docker ps --latest --quiet):/mnt/ReadMe.pdf ./
```

## Budowanie obrazu lokalnie:
```
docker build -t neo-tex-env:tl2018-fonts src/tl2018-fonts
```

## Uruchomienie kontenera z obrazu budowanego lokalnie

```
# Opcjonalnie można wyedytować skrypt który ma być uruchomiony w kontenerze:
vim src/tl2018-fonts/mnt/build.sh 

# Uruchomienie kontenera z obrazu neo-tex-env:tl2018-fonts
# z podmontowanym katalogiem /mnt
# oraz /mnt/build.sh jako entry point
docker run -it --rm -v $(pwd)/src/tl2018-fonts/mnt:/mnt neo-tex-env:tl2018-fonts bash /mnt/build.sh
```

