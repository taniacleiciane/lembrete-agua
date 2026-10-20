# Como gerar o APK sem instalar nada no PC

O APK é compilado pelo GitHub Actions. Não é preciso ter Flutter nem Android Studio.

1. Envie qualquer alteração para a branch `main`. A aba **Actions** mostra "Gerar APK" rodando.
2. Espere cerca de 5 a 10 minutos até ficar verde.
3. Abra a execução, role até **Artifacts** e baixe `lembrete-agua-apk` (um .zip com o `app-release.apk`).

## Publicar uma versão em Releases
Crie uma tag que comece com `v`, por exemplo `v1.0.0`. Pela web: **Releases → Draft a new release → Choose a tag → digite `v1.0.0` → Create new tag → Publish release**.
O workflow compila e anexa o APK à release automaticamente.

## Instalar no celular
1. Passe o `app-release.apk` para o celular (Google Drive, WhatsApp para você mesma ou cabo USB).
2. Toque no arquivo. O Android pede para **permitir instalar apps desta fonte**: permita.
3. O Play Protect pode avisar que o app é desconhecido. É normal em apps que não estão na Play Store: toque em **Instalar mesmo assim**.

## Se a pasta `.github` não subiu no upload pela web
Em **Add file → Create new file**, digite exatamente `.github/workflows/build-apk.yml`, cole o conteúdo do arquivo e confirme com **Commit changes**.
