# Changelog

Todas as mudanças importantes do CheckIn serão documentadas neste arquivo.

---

## [1.1.0] - 2026-09-28

### Adicionado

- Suporte a banners animados do Discord em GIF.
- Detecção automática do formato do card: PNG ou GIF.
- Composição de avatar, nome, usuário e informações do membro sobre banners animados.

### Melhorado

- Tree View reorganizada em português.
- Melhor organização das informações de identidade, conta Discord, servidor e cargos.
- Campos opcionais agora aparecem somente quando possuem informação.
- Melhorias no sistema de renderização dos cards.
- Melhorias no processo de reconstrução dos CheckIns.

### Corrigido

- Tratamento do `CATRACA_CHANNEL_ID` no TypeScript.
- Referência do attachment para utilizar automaticamente `checkin-profile.png` ou `checkin-profile.gif`.
- Problemas de composição e transparência durante animações GIF.

---

## [1.0.0] - 2026-09-28

### Adicionado

- Primeira versão funcional do CheckIn.
- Registro automático de novos membros.
- Card visual de perfil.
- Tree View com informações do membro.
- Comando de teste do CheckIn.
- Sincronização dos membros existentes.
- Reconstrução dos registros da catraca.
- Integração com Discord usando `discord.js`.
- Execução local com Node.js e TypeScript.