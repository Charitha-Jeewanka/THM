# CTF writeup
#ctf

### METHOD 1
1. Read the `man` pages of `dig`
2. Retrive the flag


`dig @*server_IP* -q givemetheflag.com a`
```
 <<>> DiG 9.18.0-2-Debian <<>> @10.10.149.185 -q givemetheflag.com a
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30990
;; flags: qr aa; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;givemetheflag.com.             IN      A

;; ANSWER SECTION:
givemetheflag.com.      0       IN      TXT     "flag{0767ccd06e79853318f25aeb08ff83e2}"

;; Query time: 208 msec
;; SERVER: 10.10.149.185#53(10.10.149.185) (UDP)
;; WHEN: Mon May 16 20:21:30 EDT 2022
;; MSG SIZE  rcvd: 86
```

***flag{0767ccd06e79853318f25aeb08ff83e2}***

### METHOD 2
1. Read the `man` pages of `nslookup`
2. Retrive the flag

`nslookup -type=a givemetheflag.com *server_IP*`
```
main parsing givemetheflag.com
addlookup()
make_empty_lookup()
make_empty_lookup() = 0x7fa2d799e000->references = 1
looking up givemetheflag.com
main parsing 10.10.149.185
flush_server_list()
make_server(10.10.149.185)
lock_lookup dighost.c:4184
success
start_lookup()
setup_lookup(0x7fa2d799e000)
resetting lookup counter.
cloning server list
clone_server_list()
make_server(10.10.149.185)
idn_textname: givemetheflag.com
using root origin
recursive query
add_question()
starting to render the message
done rendering
create query 0x7fa2d662d000 linked to lookup 0x7fa2d799e000
dighost.c:2083:lookup_attach(0x7fa2d799e000) = 2
dighost.c:2587:new_query(0x7fa2d662d000) = 1
do_lookup()
start_udp(0x7fa2d662d000)
dighost.c:2936:query_attach(0x7fa2d662d000) = 2
working on lookup 0x7fa2d799e000, query 0x7fa2d662d000
dighost.c:2981:query_attach(0x7fa2d662d000) = 3
unlock_lookup dighost.c:4186
dighost.c:2898:query_attach(0x7fa2d662d000) = 4
recving with lookup=0x7fa2d799e000, query=0x7fa2d662d000, handle=(nil)
recvcount=1
have local timeout of 5000
dighost.c:2847:query_attach(0x7fa2d662d000) = 5
sending a request
sendcount=1
dighost.c:1676:query_detach(0x7fa2d662d000) = 4
dighost.c:2918:query_detach(0x7fa2d662d000) = 3
send_done(0x7fa2d666b000, success, 0x7fa2d662d000)
sendcount=0
lock_lookup dighost.c:2615
success
dighost.c:2629:lookup_attach(0x7fa2d799e000) = 3
dighost.c:2648:query_detach(0x7fa2d662d000) = 2
dighost.c:2649:lookup_detach(0x7fa2d799e000) = 2
check_if_done()
list empty
unlock_lookup dighost.c:2652
recv_done(0x7fa2d666b000, success, 0x7fa2d73fa010, 0x7fa2d662d000)
lock_lookup dighost.c:3577
success
recvcount=0
dighost.c:3589:lookup_attach(0x7fa2d799e000) = 3
before parse starts
after parse
printmessage()
Server:         10.10.149.185
Address:        10.10.149.185#53

printsection()
givemetheflag.com       text = "flag{0767ccd06e79853318f25aeb08ff83e2}"
still pending.
dighost.c:4079:query_detach(0x7fa2d662d000) = 1
dighost.c:4081:_cancel_lookup()
dighost.c:2669:query_detach(0x7fa2d662d000) = 0
dighost.c:2669:destroy_query(0x7fa2d662d000) = 0
dighost.c:1634:lookup_detach(0x7fa2d799e000) = 2
check_if_done()
list empty
dighost.c:4087:lookup_detach(0x7fa2d799e000) = 1
clear_current_lookup()
dighost.c:1759:lookup_detach(0x7fa2d799e000) = 0
destroy_lookup
freeing server 0x7fa2d6612000 belonging to 0x7fa2d799e000
start_lookup()
check_if_done()
list empty
shutting down
dighost_shutdown()
unlock_lookup dighost.c:4091

done, and starting to shut down
cancel_all()
lock_lookup dighost.c:4200
success
unlock_lookup dighost.c:4231
destroy_libs()
freeing task
lock_lookup dighost.c:4251
success
flush_server_list()
destroy DST lib
unlock_lookup dighost.c:4279
Removing log context
Destroy memory
```

***flag{0767ccd06e79853318f25aeb08ff83e2}***