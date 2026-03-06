# conecteme-ds
Design System do sistema ConecteMe
# conecteme-ds

Design System do sistema ConecteMe — tokens, componentes e estilos compartilhados.

## Estrutura
```bash
src/ 
├── design-system/ ← Componentes React + CSS do DS 
│ ├── components/ ← Button, Input, Typography, Icon... 
│ └── styles/tokens/ ← CSS Custom Properties (gerado automaticamente) 
    ├── tokens/ │ └── json/ ← Fonte da verdade: JSONs exportados do Tokens Studio 
    └── styles/ ← Estilos globais da aplicação scripts/ 
    └── build-tokens.mjs ← Pipeline: JSON → CSS Custom Properties


## Pipeline de tokens

Os tokens são exportados do **Tokens Studio** (Figma) via **Luckino** e salvos em `src/tokens/json/`.
O script converte esses JSONs em CSS Custom Properties:

pnpm build:tokens
Hierarquia
Primitivos	→	Semânticos	→	CSS gerado
color-primitives-raw-colors.json		color-mode-light.json		semantic.css :root
color-mode-dark.json		semantic.css .dark
typography-desktop.json		text-styles.json		typography.css
size-desktop.json		scale-x1.json		spacing.css
elevation-mode-1.json		elevation.css
Regras de uso
Toda UI usa exclusivamente CSS variables via var() — zero valores hardcoded
Tokens importados apenas do barrel: import { ... } from '../../design-system'
Nunca criar tokens novos — apenas usar os existentes em src/design-system/styles/tokens/
Documentação completa: src/design-system/rules/
