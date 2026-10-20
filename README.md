# caza-vigia-externa

Vigia **externo** da VPS que hospeda a CAZA FILIPA e o MorSystem (auditoria de segurança, achado P2-22).

Os alertas internos rodam na própria VPS: Prometheus, Alertmanager, ntfy e Uptime Kuma. Se ela cair inteira, eles caem junto. Este repositório roda um workflow no GitHub Actions, fora da VPS, a cada 10 minutos. Ele confere a loja, o painel e o MorSystem pela internet. Se uma verificação falhar três vezes seguidas, o workflow falha e o GitHub manda e-mail ao dono.

- **Sem segredos:** só URLs públicas.
- **Público de propósito:** repositório público não consome a cota de minutos do Actions.
- **Branch padrão `vigia`:** a guarda de agentes do host reserva `main`/`master` ao responsável.
- **Inatividade:** o GitHub desativa workflows agendados de repositórios sem atividade por 60 dias. Se isso acontecer, reative em *Actions › vigia-externa › Enable workflow*.
