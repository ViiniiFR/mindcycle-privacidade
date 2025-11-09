# MindCycle Privacidade

Este repositório contém a página da **Política de Privacidade** do aplicativo MindCycle.

## Objetivo
Fornecer transparência sobre o tratamento de dados: uso local por padrão, recursos opcionais de sincronização em nuvem (Firebase) e geração de rotinas via IA (OpenAI).

## Estrutura
```
mindcycle-privacidade/
  ├─ index.html   # Página estática da política de privacidade
  └─ README.md    # Este arquivo
```

## Publicação
### Opção simples (GitHub Pages sem workflow)
1. Abra Settings > Pages.
2. Selecione Branch: `main` e Folder: `/` (root) e salve.
3. Depois de provisionado, copie a URL e mantenha o `<link rel="canonical">` em `index.html` apontando para ela.

### Opção com workflow (atualizações automáticas)
Crie (se desejar) `.github/workflows/pages.yml` com algo como:
```yaml
name: Deploy Privacy Page
on:
  push:
    branches: [ main ]
permissions:
  contents: read
  pages: write
  id-token: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v5
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./
      - name: Deploy
        uses: actions/deploy-pages@v4
```
Essa opção é útil se futuramente quiser gerar conteúdo (ex.: minificação ou múltiplas páginas).

### Teste local
Abra diretamente `index.html` no navegador (duplo clique ou via extensão Live Server). Não há build.

## Próximos Ajustes Sugeridos
- Preencher dados do Controlador/DPO (Razão Social, CNPJ, Endereço, Nome do Encarregado).
- Definir e documentar prazos de retenção e resposta a solicitações (ex.: até 15 dias).
- Confirmar se há coleta de dados de dispositivo ou analytics; se não houver, declarar explicitamente.
- Incluir histórico de versões (ex.: CHANGELOG) caso a política seja atualizada com frequência.
- Adicionar arquivo LICENSE se desejar licenciar o conteúdo (ex.: CC-BY-4.0).

## Processo de Atualização da Política
1. Criar branch (`git checkout -b update-privacy-YYYYMMDD`).
2. Editar `index.html` mantendo:
   - IDs das seções (`id="..."`) para não quebrar links.
   - Navegação `<nav>` sincronizada com novos títulos.
3. Atualizar a data em "Última atualização" e adicionar entrada no Histórico de Versões.
4. Revisar seções LGPD: Bases legais, categorias, retenção, direitos e consentimento.
5. Executar checklist abaixo.
6. Pull Request com descrição das mudanças e motivo (ex.: inclusão de publicidade personalizada, alteração de prazos).
7. Após merge na `main`, confirmar que Pages atualizou e que o canonical está correto.

### Checklist Rápido Antes de Publicar
- [ ] Data atualizada e coerente.
- [ ] Novas integrações (SDKs, APIs) descritas.
- [ ] Bases legais ajustadas (ex.: consentimento novo recurso?).
- [ ] Links externos (Firebase, OpenAI, Google Ads) funcionando.
- [ ] Prazos de retenção e resposta ainda válidos.
- [ ] Seções de direitos e contato não alteradas indevidamente.
- [ ] Canonical URL correta.

## Histórico de Versões
| Versão | Data | Principais mudanças |
|--------|------|---------------------|
| v2025-09-02 | 02/09/2025 | Versão inicial focada em uso offline e sincronização opcional. |
| v2025-11-09 | 09/11/2025 | Expansão LGPD: bases legais detalhadas, categorias adicionais, publicidade (AdMob), assinaturas, prazos (7 dias remoção, 15 dias resposta), consentimento via CMP. |

## Consentimento (CMP)
O aplicativo utiliza um gerenciador de consentimento para coletar, registrar e revogar preferências de anúncios personalizados. A política reflete esse fluxo; atualize esta seção se trocar de fornecedor ou implementar consentimento regional (ex.: GDPR/TCF).

## Boas Práticas de Contribuição
Prefira mudanças incrementais e auditáveis:
- Use mensagens de commit claras (ex.: `feat(policy): adiciona seção publicidade`).
- Evite remover IDs existentes para não quebrar âncoras externas.
- Não inclua dados sensíveis ou exemplos de chaves reais.

## Segurança & Privacidade
Este repositório não deve conter chaves privadas, tokens ou dumps de dados.

## Licença
Ainda não definida. Sugestão: adicionar `LICENSE` (ex.: Creative Commons Attribution 4.0 para texto). Caso opte por código adicional (automação), considerar MIT.

## Contribuição
Caso precise alterar a política, edite `index.html` seguindo o padrão semântico (títulos h2 com IDs, navegação no `<nav>`).

## Contato
📧 vinidevcontato1@gmail.com

---
*Última revisão deste README: 09/11/2025.*
