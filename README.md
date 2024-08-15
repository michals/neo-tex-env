# neo-tex-env

Środowisko Dockerowe do budowania śpiewnika i innych materiałów Drogi Neokatechumenalnej
dostępnych na http://spiewnik.andrzej.odyniec.info

## Budowanie obrazu:

```
docker build -t neo-tex-env:tl2018-fonts src/tl2018-fonts
```

## Uruchomienie kontenera

```
# Opcjonalnie można wyedytować skrypt który ma być uruchomiony w kontenerze:
vim src/tl2018-fonts/mnt/build.sh 

# Uruchomienie kontenera z obrazu neo-tex-env:tl2018-fonts
# z podmontowanym katalogiem /mnt
# oraz /mnt/build.sh jako entry point
docker run -it --rm -v $(pwd)/src/tl2018-fonts/mnt:/mnt neo-tex-env:tl2018-fonts bash /mnt/build.sh
```

