# Dashbutton Httpdump
 Hope this helps anyone.
### Used App / Dashbutton
* Amazon Shopping Version 8.6.35.65  Build 8.6.35.65 (Android)  
* Dashbutton JK29LP Firmware 30017420_WS

### Frist Request
Getting all wifinetworks `GET http://192.168.0.1/`

Raw
```HTTP
GET / HTTP/1.1
Content-Type: application/json
User-Agent: Dalvik/2.1.0 (Linux; U; Android 6.0.1; ONE A2003 Build/MMB29M)
Host: 192.168.0.1
Connection: Keep-Alive
Accept-Encoding: gzip

HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET, POST, OPTIONS
Access-Control-Allow-Headers: Authorization,Content-Type,Accept,Origin,User-Agent,DNT,Cache-Control,X-Mx-ReqToken,Keep-Alive,X-Requested-With,If-Modified-Since
Content-Type: text/html
Transfer-Encoding: chunked

{"amzn_devid":"G030M90363543852","amzn_macid":"De%0D%E0%92%18","international":1,"amzn_networks":[{"ssid":"Wifi1","bssid":"%C4%27%95%88_%91","security":"WPA AES PSK","rssi":"-77"},{"ssid":"Wifi2","bssid":"%08%86%3BK%9C%14","security":"WPA AES PSK","rssi":"-72"},{"ssid":"42","bssid":"%B0Hz%FA%BC%28","security":"WPA AES PSK","rssi":"-37"}],"schemes":[0]}
```
Response
```json
{
	"amzn_devid":"G030M90363543852",
	"amzn_macid":"De%0D%E0%92%18",
	"international":1,
	"amzn_networks":
	[
		{
			"ssid":"Wifi1",
			"bssid":"%C4%27%95%88_%91",
			"security":"WPA AES PSK",
			"rssi":"-77"
		},
		{
			"ssid":"Wifi2",
			"bssid":"%08%86%3BK%9C%14",
			"security":"WPA AES PSK",
			"rssi":"-72"
		},
		{
			"ssid":"42",
			"bssid":"%B0Hz%FA%BC%28",
			"security":"WPA AES PSK",
			"rssi":"-37"
		}
	],
	"schemes":[0]
}
```

### Second request
Sending public key `POST http://192.168.0.1/pubkey`

Raw
```HTTP
POST /pubkey HTTP/1.1
Content-Type: application/json
User-Agent: Dalvik/2.1.0 (Linux; U; Android 6.0.1; ONE A2003 Build/MMB29M)
Host: 192.168.0.1
Connection: Keep-Alive
Accept-Encoding: gzip
Content-Length: 210

{"publicKey":"-----BEGIN PUBLIC KEY-----\nMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEYvlUQwlgiYWepszvyQZQIVNNqEgs\niam69IOASQikAQOMTlPrCjmbyD7pKb5BzOi0aCsxI6iE2UYmqmB\/wsGvcA==\n-----END PUBLIC KEY-----\n","scheme":0}
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 0
```

Response: nothing but a HTTP 200 OK header

### Third requst
Getting public key `GET http://192.168.0.1/pubkey`

Raw
```HTTP
GET /pubkey HTTP/1.1
User-Agent: Dalvik/2.1.0 (Linux; U; Android 6.0.1; ONE A2003 Build/MMB29M)
Host: 192.168.0.1
Connection: Keep-Alive
Accept-Encoding: gzip

HTTP/1.1 200 OK
Content-Type: text/Json
Content-Length: 198

{"publicKey":"-----BEGIN PUBLIC KEY-----\nMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE8NxuOpgZBtSsUOWcCL16CevzNyq+\nrP1Co7gs4fLCOfhD8rqE3XXhhuNhCAsyfwL6v0nOnbCOi2ZQLB9EBuglTg==\n-----END PUBLIC KEY-----\n"}
```

Response:
```JSON
{
	"publicKey":"-----BEGIN PUBLIC KEY-----\nMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE8NxuOpgZBtSsUOWcCL16CevzNyq+\nrP1Co7gs4fLCOfhD8rqE3XXhhuNhCAsyfwL6v0nOnbCOi2ZQLB9EBuglTg==\n-----END PUBLIC KEY-----\n"
}
```

### Fourth request

setting locale `POST http://192.168.0.1/locale`

Raw
```HTTP
POST /locale HTTP/1.1
Content-Type: application/json
User-Agent: Dalvik/2.1.0 (Linux; U; Android 6.0.1; ONE A2003 Build/MMB29M)
Host: 192.168.0.1
Connection: Keep-Alive
Accept-Encoding: gzip
Content-Length: 30

{"cc":"DE","realm":"DEAmazon"}
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 0
```
Response: Header 200 OK 


### Fith request
setting token `POST http://192.168.0.1/stoken`

Raw
```HTTP
POST /stoken HTTP/1.1
Content-Type: application/octet-stream
User-Agent: Dalvik/2.1.0 (Linux; U; Android 6.0.1; ONE A2003 Build/MMB29M)
Host: 192.168.0.1
Connection: Keep-Alive
Accept-Encoding: gzip
Content-Length: 77

.......L._.N:I....c.....G....|?L_w..}...$..%..,.O.........A....5...b.......$.
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 0
´´´
Response: Header 200 OK 

### Sixth request

configures the network
`POST http://192.168.0.1/network`

Raw
```HTTP
POST /network HTTP/1.1
Content-Type: application/octet-stream
User-Agent: Dalvik/2.1.0 (Linux; U; Android 6.0.1; ONE A2003 Build/MMB29M)
Host: 192.168.0.1
Connection: Keep-Alive
Accept-Encoding: gzip
Content-Length: 104

...7d....G]...c[X.l...z.MI...@.Q.j......?Xi<.b2....z..5.>Zx..ETq{s.5.*....k...w..#.P=........`J...bu....HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 0
```
Response: nothing but a HTTP 200 OK header. The header will be 200 OK everytime, even the SSID or password is wrong
