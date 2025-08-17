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
3. Dans Coolify : **Create New Resource → Docker Compose (from Git)**  
- Base Directory: `/monitoring/netdata`  
- Compose file: `/compose.yml`  
- Renseigner `DOMAIN_NETDATA` / `TZ` dans l’onglet **Environment**.  
- **Connect to Predefined Network**: `coolify` (si non déclaré dans le compose).  
- **Deploy**.

4. Ouvrir `https://<DOMAIN_NETDATA>` → dashboard Netdata.

## Dépannage
- 404 Traefik: vérifier `DOMAIN_NETDATA` et la connexion au réseau `coolify`.
- Page blanche / “No available server” : vérifier que le conteneur est **healthy**.
- Pas de métriques host: vérifier les montages `/proc`, `/sys`, `/etc/passwd`, `/etc/group` en RO.

## Références
- Coolify — Build Pack Docker Compose & labels Traefik.  
- Traefik — Provider Docker & labels (rule/entryPoints/port).  
- Netdata — Installation Docker (montages / droits).
