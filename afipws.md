# Afip WS

## Artículos básicos

- [PyAfipWs: facilitando, extendiendo y liberando los Servicios Web de AFIP](http://www.web2py.com.ar/wiki/default/_page/PyAfipWs)

## Videos Basicos
- [Habilitación de Factura Electrónica en AFIP (1° Parte)](https://www.youtube.com/watch?v=np6zxGb75Jw)


## Generacion de Certificados

Siguiendo el siguiente instrusctivo [cert-req-howto.txt](http://www.afip.gov.ar/ws/WSAA/cert-req-howto.txt)

```bash
openssl genrsa -out nosotros.key 1024
openssl req -new -key nosotros.key -subj "/C=AR/O=Cristian Cortez/CN=certificado1/serialNumber=CUIT 20330114534" -out nosotros.csr
```

## Test Suite

- [TrazaMed](https://github.com/reingart/pyafipws/blob/master/tests/trazamed.py)
