# Vetur AI Agent Instructions

## Project Overview
Vetur es una extensión de VS Code para desarrollo Vue.js que proporciona:
- Servidor de lenguaje Vue (VLS) en `/server`
- Interfaz de terminal Vetur (VTI) en `/vti`
- Cliente VS Code en `/client`

## Arquitectura Clave
1. **Language Server Protocol (LSP)**:
   - El servidor VLS (`/server/src/`) implementa LSP para proporcionar características de IDE
   - El cliente VS Code (`/client/`) se comunica con VLS a través del protocolo LSP
   - Referencia: `/server/src/vueServerMain.ts` para el punto de entrada del servidor

2. **Procesamiento de Archivos Vue**:
   - Los archivos `.vue` se procesan como bloques de template/script/style
   - Ver `/server/src/modes/` para el manejo de diferentes lenguajes dentro de archivos Vue

## Flujos de Desarrollo Críticos

1. **Build y Watch**:
   ```bash
   yarn install         # Instala dependencias 
   yarn compile        # Build único
   yarn watch          # Build en modo watch
   ```

2. **Testing**:
   - Tests de servidor: `yarn test:server`
   - Tests E2E: `yarn test:e2e`
   - Tests de gramática: `yarn test:grammar`

## Convenciones de Código

1. **TypeScript**:
   - Usar tipos estrictos - ver ejemplos en `/server/src/types.ts`
   - Seguir configuración en `tsconfig.json` y `tslint.json`

2. **Organización del Código**:
   - Servicios en `/server/src/services/`
   - Modos de lenguaje en `/server/src/modes/`
   - Comandos del cliente en `/client/commands/`

3. **Gramáticas**:
   - Archivos TextMate en `/syntaxes/`
   - Generados vía `yarn build:grammar`

## Patrones de Integración

1. **Configuración**:
   - Configuraciones de extensión en `package.json` bajo `contributes.configuration`
   - Ver `/server/src/config.ts` para manejo de configuración

2. **Diagnósticos**:
   - Implementar validaciones en modos específicos de lenguaje
   - Emitir diagnósticos a través del protocolo LSP
   - Ejemplos en `/server/src/modes/*/languageService.ts`

## Notas Importantes

1. **Bloques Personalizados**:
   - Configurados en `vetur.grammar.customBlocks`
   - Ver `/server/src/modes/template/` para implementación

2. **Referencias Clave**:
   - `/README.md` - Documentación principal
   - `/docs/` - Guías detalladas
   - `/rfcs/` - Propuestas de cambios mayores

Cualquier modificación debe seguir las guías en `.github/CONTRIBUTING.md`.