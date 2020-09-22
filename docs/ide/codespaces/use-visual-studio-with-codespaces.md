---
title: Visual Studio z codespace (wersja zapoznawcza)
description: Dowiedz się więcej na temat używania środowiska IDE programu Visual Studio z usługą GitHub Codespaces na potrzeby programowania systemu Windows.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: c3a2e14236c2d24bc9650fab81150cc295826844
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006257"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>Jak używać programu Visual Studio z codespace (wersja zapoznawcza)

Program Visual Studio ma doskonałą obsługę tworzenia aplikacji w witrynie GitHub Codespaces. Możesz tworzyć i łączyć się z codespace oraz korzystać z pełnych możliwości programu Visual Studio do pracy nad projektami w zdalnym, hostowanym środowisku. Mimo że Twój kod źródłowy i narzędzia znajdują się w codespace, a Twoje kompilacje i debugowanie są wykonywane w chmurze, środowisko programistyczne będzie działać tak szybko i bez problemów jak w przypadku pracy lokalnie. Możesz korzystać z codespace z poziomu wersji zapoznawczej programu Visual Studio 2019 ([Utwórz konto w celu uzyskania ograniczonej publicznej wersji beta](https://github.com/features/codespaces/signup-vs)).

> [!NOTE]
> W tym artykule opisano sposób korzystania z programu Visual Studio w celu nawiązania połączenia z usługą GitHub Codespaces. Możesz dowiedzieć się więcej o łączeniu się z codespace innymi klientami w dokumentacji [Visual Studio Code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) lub [GitHub](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace) .

> [!NOTE]
> Jeśli nie masz już zainstalowanego [programu Visual Studio 2019 Preview](https://aka.ms/vspreview) , możesz pobrać go z [VisualStudio.Microsoft.com](https://aka.ms/vspreview).

## <a name="enable-connect-to-github-codespaces"></a>Włączanie połączenia z usługą GitHub Codespaces

Łączenie z usługą GitHub Codespaces za pomocą programu Visual Studio 2019 Preview nie jest domyślnie włączone, więc najpierw musisz włączyć opcję wersji zapoznawczej.

1. W wersji zapoznawczej programu Visual Studio **Tools**2019 Użyj  >  elementu menu**Opcje** narzędzi, aby otworzyć okno dialogowe Opcje.

2. W obszarze **środowisko**wybierz pozycję **funkcje w wersji zapoznawczej** i Sprawdź funkcję **Połącz z usługą GitHub Codespaces** w wersji zapoznawczej.

   ![Sprawdź funkcję Connect Codespaces w wersji zapoznawczej](media/connect-to-github-codespaces-preview-feature.png)

3. Aby funkcja była dostępna, konieczne będzie ponowne uruchomienie programu Visual Studio.

## <a name="create-a-codespace"></a>Utwórz codespace

Jeśli nie masz jeszcze elementu codespace, możesz go utworzyć z poziomu programu Visual Studio.

1. Po uruchomieniu programu Visual Studio w oknie startowym zostanie wyświetlony przycisk **Połącz z codespaceą** w obszarze "wprowadzenie".

   ![Okno uruchamiania programu Visual Studio z połączeniem z codespace](media/visual-studio-start-window.png)

2. Wybierz pozycję **Połącz z codespaceą** . zostanie wyświetlony monit o zalogowanie się do usługi GitHub. Możesz również utworzyć konto usługi GitHub, jeśli jeszcze go nie masz.

   ![Logowanie do usługi GitHub w programie Visual Studio](media/visual-studio-sign-in-to-github.png)

   Po wybraniu opcji **Zaloguj się do usługi GitHub**postępuj zgodnie z przepływem pracy logowania w witrynie GitHub online.

3. Jeśli nigdy nie utworzono elementu codespace, zostanie wyświetlony monit o jego utworzenie.

   W obszarze "Szczegóły Codespace" należy podać **adres URL repozytorium**. Codespaces usługi GitHub spowoduje sklonowanie określonego repozytorium do codespace podczas jego tworzenia.

   Możesz również zmodyfikować **Typ wystąpienia** i **wstrzymać po** przekroczeniu limitu czasu za pośrednictwem ich list rozwijanych. Po ustawieniu szczegółów codespace wybierz przycisk **Utwórz i Połącz** .

   ![Szczegóły programu Visual Studio codespace](media/visual-studio-codespace-details.png)

   Codespaces GitHub rozpocznie przygotowywanie codespace i otwarcie programu Visual Studio, gdy codespace będzie gotowa.

   Nazwa codespace zostanie wyświetlona w zdalnym wskaźniku na pasku menu.

   ![Program Visual Studio połączony z repozytorium eShopOnWeb codespace](media/visual-studio-eshoponweb-codespace.png)

4. Zacznij korzystać z programu Visual Studio, tak jak w przypadku pracy lokalnie. Co należy zrobić:

   * Przeglądaj kod źródłowy.
   * Wybierz plik rozwiązania i skompiluj rozwiązanie (**Ctrl + Shift + B**).
   * Ustaw punkt przerwania w pliku źródłowym i naciśnij klawisz **F5** , aby uruchomić aplikację w debugerze.
   * Wprowadź zmiany i zatwierdź je w repozytorium.   

> [!NOTE]
> W tej chwili nie można utworzyć usługi GitHub Codespaces dla programu Visual Studio za pomocą [portalu GitHub Codespaces](https://github.com/codespaces). Można je tworzyć tylko przy użyciu programu Visual Studio.

## <a name="connect-to-a-codespace"></a>Nawiązywanie połączenia z usługą codespace

Po utworzeniu codespace możesz otworzyć swój codespace bezpośrednio z programu Visual Studio.

1. Po uruchomieniu programu Visual Studio w oknie startowym zostanie wyświetlony przycisk **Połącz z Codespaceą** w obszarze "wprowadzenie".

   ![Okno uruchamiania programu Visual Studio z połączeniem z codespace](media/visual-studio-start-window.png)

   Jeśli jesteś już w programie Visual Studio, możesz użyć **pliku**  >  **Connect to Codespace** .

   ![Plik programu Visual Studio — łączenie z elementem menu codespace](media/visual-studio-file-connect-to-codespace.png)

2. Wybierz pozycję **Połącz z codespace**. Użytkownik zostanie poproszony o zalogowanie się do usługi GitHub, jeśli jeszcze tego nie zrobiono.

3. Zobaczysz teraz wszystkie Twoje codespaces w serwisie GitHub wraz ze szczegółami przedstawionymi w prawym panelu.

   ![Program Visual Studio wyświetlający dostępne codespaces usługi GitHub i szczegółowe informacje](media/visual-studio-connect-codespace.png)

   Wszystkie codespaces Sklonowane repozytorium Azure DevOps będą widoczne tylko w programie Visual Studio, a nie na stronie Codespaces w witrynie GitHub.

4. Wybierz codespace i wybierz przycisk **Połącz** . Jeśli codespace została wstrzymana, zostanie ponownie uruchomiona, a program Visual Studio zostanie otwarty z tym codespace.

   Nazwa codespace zostanie wyświetlona w zdalnym wskaźniku na pasku menu.

   ![Program Visual Studio połączony z repozytorium eShopOnWeb codespace](media/visual-studio-eshoponweb-codespace.png)

5. Zacznij korzystać z programu Visual Studio, tak jak w przypadku pracy lokalnie. Co należy zrobić:

   * Przeglądaj kod źródłowy.
   * Wybierz plik rozwiązania i skompiluj rozwiązanie (**Ctrl + Shift + B**).
   * Ustaw punkt przerwania w pliku źródłowym i naciśnij klawisz **F5** , aby uruchomić aplikację w debugerze.
   * Wprowadź zmiany i zatwierdź je w repozytorium.

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>Zobacz też

* [Co to jest GitHub Codespaces?](codespaces-overview.md)
* [Jak dostosować codespace](customize-codespaces.md)
* [Obsługiwane funkcje programu Visual Studio](supported-features-codespaces.md)
