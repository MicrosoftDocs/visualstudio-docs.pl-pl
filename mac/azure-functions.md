---
title: Wprowadzenie do usługi Azure Functions
description: Korzystanie z funkcji platformy Azure w programie Visual Studio dla komputerów Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: dac6a1c53cea8982a75c7b12661c98f2feb37f83
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "73189657"
---
# <a name="introduction-to-azure-functions"></a>Wprowadzenie do usługi Azure Functions

Funkcje platformy Azure to sposób tworzenia i uruchamiania fragmentów kodu sterowanych zdarzeniami — funkcjami — w chmurze, bez konieczności jawnego udostępniania infrastruktury lub zarządzania nią. Aby uzyskać więcej informacji na temat usług Azure Functions, zobacz [dokumentację usługi Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Wymagania

Narzędzia funkcji platformy Azure są zawarte w **programie Visual Studio dla komputerów Mac 7.5** i nowszych.

Aby utworzyć i wdrożyć funkcje, potrzebujesz również subskrypcji platformy Azure. Jeśli nie masz konta platformy Azure, możesz zarejestrować się już dziś za darmo i otrzymać 12 miesięcy bezpłatnych popularnych usług, 200 dolarów bezpłatnego kredytu i 25+ zawsze darmowe usługi [https://azure.com/free](https://azure.com/free/dotnet)->.

## <a name="creating-your-first-azure-functions-project"></a>Tworzenie pierwszego projektu usługi Azure Functions

1. W programie Visual Studio dla komputerów Mac wybierz pozycję **Plik > nowe rozwiązanie**.
2. W oknie dialogowym Nowy projekt wybierz szablon Usługi Azure w obszarze **Cloud > General** i kliknij przycisk **Dalej:**

    ![Okno dialogowe Nowy projekt z opcją funkcji platformy Azure](media/azure-functions-image1.png)

3. Wybierz początkowy szablon usługi Azure Functions, którego chcesz użyć, wprowadź nazwę funkcji i kliknij przycisk **Dalej**.

    ![Nowe okno dialogowe projektu z szablonami funkcji platformy Azure](media/azure-functions-image2.png)

    > [!TIP]
    > Podczas gdy dołączone środowisko uruchomieniowe usługi Azure Functions i szablony (CLI) są przechowywane na bieżąco, jak to możliwe, nieuchronnie stają się przestarzałe. Podczas tworzenia nowego projektu funkcji program Visual Studio dla komputerów Mac sprawdza dostępność aktualizacji interfejsu wiersza polecenia i powiadomi Cię, jak pokazano na poniższej ilustracji. Wystarczy kliknąć przycisk, aby pobrać zaktualizowane szablony.
    > ![Dostępne jest nowe okno dialogowe projektu z aktualizacjami funkcji platformy Azure](media/azure-functions-update.png)

    W zależności od wybranego typu funkcji następna strona wyświetli monit o wprowadzenie szczegółów, takich jak prawa dostępu, jak pokazano na poniższej ilustracji:

    ![Okno dialogowe Nowy projekt z dodatkową opcją](media/azure-functions-image3.png)

    Aby uzyskać więcej informacji na temat różnych typów szablonów usługi Azure Functions i właściwości powiązania wymagane do skonfigurowania każdego szablonu, zobacz [sekcję Dostępne szablony funkcji.](#available-function-templates) W tym przykładzie używamy wyzwalacza http z prawami dostępu ustawionymi na anonimowe.

4. Po ustawieniu parametrów wybierz lokalizację projektu i kliknij przycisk **Utwórz**.

Program Visual Studio dla komputerów Mac tworzy projekt .NET Standard z włączoną funkcją domyślną. Zawiera również odwołania NuGet do różnych pakietów **AzureWebJobs,** a także pakiet **Newtonsoft.Json.**

![Edytor programu Visual Studio dla komputerów Mac wyświetlający zupełnie nową funkcję platformy Azure z szablonu](media/azure-functions-newproj.png)

Nowy projekt zawiera następujące pliki:

* **your-function-name.cs** — ta klasa zawiera kod standardowy dla wybranej funkcji. Zawiera atrybut **FunctionName** o nazwie funkcji oraz atrybut wyzwalacza, który określa, co wyzwala funkcję (np. żądanie HTTP). Aby uzyskać więcej informacji na temat metody funkcji, zapoznaj się z artykułem [referencyjnym dla deweloperów usług Azure Functions C#.](/azure/azure-functions/functions-dotnet-class-library)
* **host.json** — ten plik opisuje opcje konfiguracji globalnej dla hosta funkcji. Przykładowy plik i informacje o dostępnych ustawieniach tego pliku można znaleźć w [odwołani host.json dla usługi Azure Functions](/azure/azure-functions/functions-host-json).
* **local.settings.json** — ten plik zawiera wszystkie ustawienia uruchamiania funkcji lokalnie. Te ustawienia są używane przez narzędzia podstawowe usług Azure Functions Core. Aby uzyskać więcej informacji, zobacz [plik ustawień lokalnych](/azure/azure-functions/functions-run-local#local-settings-file) w artykule Narzędzia podstawowe usług Azure Functions.

Po utworzeniu nowego projektu usługi Azure Functions w programie Visual Studio dla komputerów Mac można przetestować domyślną funkcję wyzwalaną przez protokół HTTP z komputera lokalnego.

## <a name="testing-the-function-locally"></a>Testowanie funkcji lokalnie

Dzięki obsłudze funkcji platformy Azure w programie Visual Studio dla komputerów Mac można testować i debugować funkcję na lokalnym komputerze deweloperskim.

1. Aby przetestować funkcję lokalnie, naciśnij przycisk **Uruchom** w programie Visual Studio dla komputerów Mac:

    ![Przycisk Rozpocznij debugowanie w programie Visual Studio dla komputerów Mac](media/azure-functions-run.png)

1. Uruchamianie projektu rozpoczyna debugowanie lokalne w usłudze Azure Function i otwiera nowe okno terminala, jak pokazano na poniższej ilustracji:

    ![okno terminala z wyjściem funkcji](media/azure-functions-terminal.png)

    Skopiuj adres URL z danych wyjściowych.

3. Wklej adres URL żądania HTTP w pasku adresu przeglądarki. Dodaj ciąg `?name=<yourname>` zapytania na końcu adresu URL i wykonaj żądanie. Na poniższej ilustracji przedstawiono odpowiedź w przeglądarce na lokalne żądanie GET zwrócone przez funkcję:

    ![żądanie http w przeglądarce](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Dodawanie innej funkcji do projektu

Szablony funkcji umożliwiają szybkie tworzenie nowych funkcji przy użyciu najczęściej stosowanych wyzwalaczy i szablonów. Aby utworzyć inny typ funkcji, wykonaj następujące czynności:

1. Aby dodać nową funkcję, kliknij prawym przyciskiem myszy nazwę projektu i wybierz polecenie **Dodaj > Dodaj funkcję...**:

    ![akcja kontekstowa do dodawania nowej funkcji](media/azure-functions-addnew.png)

2. W oknie dialogowym **Nowa funkcja platformy Azure** wybierz wymagany przez Ciebie funkcję:

    ![nowe okno dialogowe funkcji platformy Azure](media/azure-functions-image4.png)

    Lista szablonów funkcji platformy Azure znajdują się w sekcji [Dostępne szablony funkcji.](#available-function-templates)

Powyższa procedura służy do dodawania większej liczby funkcji do projektu aplikacji funkcji. Każda funkcja w projekcie może mieć inny wyzwalacz, ale funkcja musi mieć dokładnie jeden wyzwalacz. Aby uzyskać więcej informacji, zobacz [Usługi Azure Functions wyzwalania i pojęć powiązań](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publikowanie na platformie Azure

1. Kliknij prawym przyciskiem myszy nazwę projektu i wybierz ![opcję **Publikuj > Publikuj na platformie Azure:** Publikuj na platformie Azure.](media/azure-functions-image5.png)
2. Jeśli twoje konto platformy Azure jest już połączone z programem Visual Studio dla komputerów Mac, zostanie wyświetlona lista dostępnych usług aplikacji. Jeśli nie zalogowałeś się, zostanie wyświetlony monit o zrobienie tego.
3. W oknie dialogowym **Publikuj do usługi Azure App Service** możesz wybrać istniejącą usługę aplikacji lub utworzyć nową, klikając przycisk **Nowy**.
4. W oknie dialogowym Tworzenie nowej usługi ![ **aplikacji** wprowadź ustawienia: Opublikuj w menu azure](media/azure-functions-image7.png)

    |Ustawienie  |Opis  |
    |---------|---------|
    |**Nazwa usługi aplikacji**|Globalnie unikatowa nazwa identyfikująca nową aplikację funkcji.|
    |**Subskrypcja**|Subskrypcja platformy Azure, która ma być używana.|
    |**[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)**|Nazwa grupy zasobów, w której ma zostać utworzona aplikacja funkcji. Wybierz, **+** aby utworzyć nową grupę zasobów.|
    |**[Plan serwisowy](/azure/azure-functions/functions-scale)**|Wybierz istniejący plan lub utwórz plan niestandardowy. Wybierz lokalizację w regionie w pobliżu lub w pobliżu innych usług, do których mają dostęp funkcje.|

5. Kliknij **przycisk Dalej,** aby utworzyć konto magazynu. Środowisko uruchomieniowe usługi Functions wymaga konta magazynu platformy Azure. Kliknij **przycisk Niestandardowy,** aby utworzyć konto magazynu ogólnego przeznaczenia, lub użyj istniejącego:

    ![Opcja menu publikowania na platformie azure](media/azure-functions-image8.png)

6. Kliknij przycisk **Utwórz**, aby utworzyć aplikację funkcji i powiązane zasoby na platformie Azure przy użyciu tych ustawień i wdrożyć kod projektu funkcji.

7. Może zostać wyświetlony monit z okna dialogowego podczas publikowania informujące o "Aktualizacja wersji funkcji na platformie Azure". Kliknij **przycisk Tak**:

    ![Opcja menu publikowania na platformie azure](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Ustawienia aplikacji funkcji

Wszystkie ustawienia dodane w local.settings.json muszą również zostać dodane do aplikacji funkcji na platformie Azure. Te ustawienia nie są przekazywane automatycznie podczas publikowania projektu.

Aby uzyskać dostęp do ustawień aplikacji, [https://ms.portal.azure.com/](https://ms.portal.azure.com/)przejdź do witryny Azure portal pod adresem . W obszarze **Aplikacje funkcji**wybierz **pozycję Aplikacje funkcyjne** i podświetl nazwę funkcji:

![menu funkcji azure](media/azure-functions-image9.png)

Na karcie **Przegląd** wybierz **pozycję Ustawienia aplikacji** w obszarze **Skonfigurowane funkcje:**

![Za pomocą karty funkcji platformy Azure](media/azure-functions-image10.png)

W tym miejscu można ustawić ustawienia aplikacji dla aplikacji funkcyjnej, w której można dodawać nowe ustawienia aplikacji lub modyfikować istniejące:

![obszar ustawień aplikacji w witrynie Azure portal](media/azure-functions-image11.png)

Jednym z ważnych ustawień, `FUNCTIONS_EXTENSION_VERSION`które może być konieczne do ustawienia jest . Podczas publikowania z programu Visual Studio dla komputerów Mac wartość ta powinna być ustawiona na **wersję beta**.

## <a name="available-function-templates"></a>Dostępne szablony funkcji

- **Wyzwalacz GitHub** — odpowiadaj na zdarzenia występujące w repozytoriach Usługi GitHub. Aby uzyskać więcej informacji, zobacz [artykuł usługi Azure Functions w usłudze GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
  - GitHub commenter — ta funkcja zostanie uruchomiony po otrzymaniu elementu webhook GitHub dla żądania problemu lub ściągnięcia i dodaje komentarz.
  - GitHub WebHook — ta funkcja zostanie uruchomiony po odebraniu elementu webhook GitHub.

- **HTTP** — wyzwalanie wykonywania kodu przy użyciu żądania HTTP. Istnieją jawne szablony dla następujących wyzwalaczy HTTP:
  - Wyzwalacz http
  - Http GET CRUD
  - Http POST CRUD
  - Wyzwalacz http z parametrami

- **Timer** — wykonywanie oczyszczania lub innych zadań wsadowych zgodnie ze wstępnie zdefiniowanym harmonogramem. Ten szablon zawiera dwa pola: Nazwa i harmonogram, który jest wyrażeniem cron sześciu pól. Aby uzyskać więcej informacji, zobacz [artykuł o funkcjach platformy Azure w sprawie czasu](/azure/azure-functions/functions-create-scheduled-function)

- **Kolejka wyzwalacza** — jest to funkcja, która będzie reagować na wiadomości po ich przybyciu w kolejce usługi Azure Storage. Oprócz nazwy funkcji ten szablon przyjmuje **path** (nazwę kolejki, z której zostanie odczytany komunikat) i konto magazynu **Connection** (nazwa ustawienia aplikacji zawierającego parametry połączenia konta magazynu). Aby uzyskać więcej informacji, zobacz [artykuł o funkcjach platformy Azure dotyczący Magazynu kolejek](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Wyzwalacz obiektu blob** — przetwarzaj obiekty BLOB usługi Azure Storage po dodaniu ich do kontenera. Oprócz nazwy funkcji ten szablon przyjmuje również właściwość ścieżki i połączenia. Właściwość path jest ścieżką na koncie magazynu, którą będzie monitorować wyzwalacz. Konto połączenia to nazwa ustawienia aplikacji zawierającego parametry połączenia konta magazynu. Aby uzyskać więcej informacji, zobacz [artykuł usługi Usługi Azure funkcje Blob Storage](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Ogólny element WebHook** — jest to prosta funkcja, która będzie uruchamiana za każdym razem, gdy otrzyma żądanie od dowolnej usługi obsługującej pliki webhook. Aby uzyskać więcej informacji, zobacz [artykuł o funkcjach platformy Azure dotyczący ogólnych elementów webhook](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Aranżacja trwałych funkcji** — funkcje trwałe umożliwiają pisanie funkcji stanowych w środowisku bezserwerowym. Rozszerzenie zarządza stanem, punktami kontrolnymi i ponownym uruchamianiem. Aby uzyskać więcej informacji, zobacz przewodniki funkcji platformy Azure dotyczące [funkcji trwałych.](/azure/azure-functions/durable-functions-overview)

- **Ponowne odtwarzanie obrazu** — ta funkcja tworzy obrazy o przemalowanej rozmiarze za każdym razem, gdy obiekt blob jest dodawany do kontenera. Szablon pobiera ścieżkę i ciąg połączenia dla wyzwalacza, małe dane wyjściowe obrazu i średnie dane wyjściowe obrazu.

- **Token sygnatury dostępu** Współdzielonego — ta funkcja generuje token sygnatury dostępu Współdzielonego dla danego kontenera usługi Azure Storage i nazwy obiektu blob. Oprócz nazwy funkcji ten szablon przyjmuje również właściwość ścieżki i połączenia. Właściwość path jest ścieżką na koncie magazynu, którą będzie monitorować wyzwalacz. Konto połączenia to nazwa ustawienia aplikacji zawierającego parametry połączenia konta magazynu. Należy również ustawić **prawa dostępu.** Poziom autoryzacji określa, czy funkcja wymaga klucza interfejsu API i który klucz do użycia; Funkcja używa klawisza funkcyjnego; Administrator używa klucza głównego. Aby uzyskać więcej informacji, zobacz [C# Funkcja platformy Azure do generowania przykład tokenów sygnatury](https://github.com/Azure-Samples/functions-dotnet-sas-token/) dostępu Współdzielonego.
