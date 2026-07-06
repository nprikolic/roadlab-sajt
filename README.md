# roadlab-sajt

Homepage / landing za **roadlab.rs**. Čista statika (HTML/CSS, bez build koraka) —
servira je Caddy na serveru *boombox*.

## Fajlovi
- `index.html` — homepage (mesta za izmenu obeležena `EDIT ME` komentarima)
- `style.css` — stilovi (bez frameworka)

## Lokalni pregled
Otvori `index.html` u browseru, ili posluži folder:
```
python -m http.server 8080
```
Napomena: link `/marwis/` radi tek na serveru (tamo živi MARWIS mapa iz zasebnog repoa);
lokalno će biti 404, što je očekivano.

## Deploy (boombox)
Sajt se na server povlači kao i ostali — `sites/` na boombox-u je za svaki sajt
zaseban repo, kloniran preko HTTPS-a, a Caddy servira `roadlab.rs/` iz `/srv/roadlab-sajt`.

```
# jednokratno, na serveru:
git -C /opt/boombox/sites clone https://github.com/nprikolic/roadlab-sajt.git

# svaki naredni deploy:
git -C /opt/boombox/sites/roadlab-sajt pull
```
Caddy servira izmene odmah (statika, bez reload-a). Ruta `/marwis` ostaje iz svog repoa.
