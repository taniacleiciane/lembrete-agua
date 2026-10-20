# Lembrete de Água

App Android que avisa, todos os dias, a hora de beber um copo de água (250 mL). São 14 lembretes entre 7h e 22h, o que dá 3,5 L por dia.

<!-- ![Tela do app](docs/tela.png) -->

Nasceu de uma necessidade pessoal: eu usava um calendário `.ics` com alarmes de água, mas queria avisos que não dependessem do app de agenda. O app foi escrito do zero, compilado na nuvem e instalado no meu próprio celular.

## O que ele faz
- Agenda 14 notificações diárias (07h, 08h, 09h, 10h, 11h, 12h, 14h, 15h, 16h, 17h, 18h, 19h, 21h e 22h), repetidas todos os dias.
- Usa o fuso `America/Sao_Paulo`, então o horário não muda se o celular trocar de fuso.
- Pede a permissão de **alarmes exatos** do Android quando necessário e avisa se os lembretes podem atrasar.
- Tem botão para ativar, desativar e enviar uma notificação de teste.

## Tecnologias
Flutter e Dart, `flutter_local_notifications`, `timezone` e GitHub Actions para gerar o APK sem instalar nada no computador.

## Como o projeto está organizado
| Caminho | Função |
|---|---|
| `lib/main.dart` | Tela, agendamento das notificações e leitura do estado |
| `pubspec.yaml` | Dependências |
| `tool/patch_android.py` | Ajusta o projeto Android gerado (permissões, desugaring, nome do app) |
| `.github/workflows/build-apk.yml` | Compila o APK e publica em Releases quando há tag `v*` |
| `docs/GERAR_APK.md` | Passo a passo para gerar e instalar o APK |

A pasta `android/` não fica versionada: o workflow a cria com `flutter create` a cada build.

## Instalar
Baixe o `app-release.apk` na aba **Releases** e siga o passo a passo em [docs/GERAR_APK.md](docs/GERAR_APK.md).

Em alguns celulares (Xiaomi, Samsung, Motorola), vá em Configurações → Apps → Água → Bateria → **Sem restrições**. Senão o sistema pode segurar os avisos.

## Personalizar
Edite `horarios` e `mlPorCopo` no topo de `lib/main.dart` e envie para a branch `main`: um APK novo é gerado sozinho.

## Limitações e próximos passos
- Os horários ainda são fixos no código. Próximo passo: permitir escolher horários e o tamanho do copo dentro do app.
- Não há registro de quantos copos foram bebidos nem testes automatizados.
- Só Android.

## Licença
MIT. Veja [LICENSE](LICENSE).
