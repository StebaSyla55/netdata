# netdata
netdata pour monitorer (à déployer depuis coolify) 

# Netdata (simple) via Coolify + Traefik

## Objectif
Déployer un Netdata **par serveur** (VPS, ACEMAGICIAN), sans parent/enfant, routé par Traefik (Coolify) derrière un tunnel Cloudflare wildcard. Aucune exposition de port.

## Prérequis
- Coolify opérationnel avec proxy Traefik (`coolify-proxy`) et Tunnel Cloudflare pointant vers `http://coolify-proxy:80`.
- Le réseau Docker `coolify` présent.
- Un domaine par serveur (ex. `netdata.XXX.COM`, `netdata-acm.XXX.COM`).

## Déploiement

