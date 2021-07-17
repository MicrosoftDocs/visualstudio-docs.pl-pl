---
title: Azure Functions w systemie MacOs
description: Wprowadzenie do Azure Functions w Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 04/02/2021
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: a91c40d0b6fe09aa88c0f3d72d21abde10621b5e
ms.sourcegitcommit: 879b11112c775a1c1dd9ebd4e59a3d0caec84220
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2021
ms.locfileid: "114397190"
---
# <a name="introduction-to-azure-functions"></a>Wprowadzenie do usługi Azure Functions

Azure Functions to sposób tworzenia i uruchamiania opartych na zdarzeniach fragmentów kodu — funkcji — w chmurze bez konieczności jawnego aprowizować infrastruktury ani zarządzać infrastrukturą. Aby uzyskać więcej informacji na temat usługi Azure Functions, zapoznaj się z [dokumentacją usługi Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Wymagania

Narzędzia funkcji platformy Azure są dostępne **w Visual Studio dla komputerów Mac 7.5** i nowszej wersji.

Do tworzenia i wdrażania funkcji potrzebna jest również subskrypcja platformy Azure. Jeśli nie masz konta platformy Azure, możesz zarejestrować się bezpłatnie już dzisiaj i otrzymać 12-miesięcy bezpłatnych popularnych usług, 200 USD bezpłatnych środków i 25+ zawsze bezpłatnych usług — > [https://azure.com/free](https://azure.com/free/dotnet) .

## <a name="creating-your-first-azure-functions-project"></a>Tworzenie pierwszego Azure Functions projektu

1. W Visual Studio dla komputerów Mac wybierz **pozycję Plik > nowe rozwiązanie.**
2. W oknie dialogowym Project wybierz szablon Azure Functions w obszarze **Cloud > Ogólne** i kliknij przycisk **Dalej:**

    ![Nowe Project dialogowe z wyświetloną Azure Functions oknie dialogowym](media/azure-functions-image1.png)

3. Wybierz początkowy szablon Azure Functions, który chcesz użyć, wprowadź nazwę funkcji i kliknij przycisk **Dalej.**

    ![Nowe Project dialogowe z Azure Functions szablonów](media/azure-functions-image2.png)

    > [!TIP]
    > Chociaż środowisko uruchomieniowe Azure Functions i szablony (CLI) są aktualne, są zawsze nieaktualne. Podczas tworzenia nowego projektu funkcji program Visual Studio dla komputerów Mac aktualizacje interfejsu wiersza polecenia i powiadomi Cię, jak pokazano na poniższej ilustracji. Po prostu kliknij przycisk , aby pobrać zaktualizowane szablony.
    > ![Okno dialogowe nowego projektu z Azure Functions są dostępne aktualizacje](media/azure-functions-update.png)

    W zależności od wybranego typu funkcji na następnej stronie zostanie wyświetlony monit o wprowadzenie szczegółów, takich jak prawa dostępu, jak pokazano na poniższej ilustracji:

    ![Nowe Project dialogowe z dodatkową opcją](media/azure-functions-image3.png)

    Aby uzyskać więcej informacji na temat różnych typów szablonów Azure Functions i właściwości powiązania wymaganych do skonfigurowania każdego szablonu, zobacz sekcję [Dostępne szablony funkcji.](#available-function-templates) W tym przykładzie używamy wyzwalacza Http z prawami dostępu ustawionymi na anonimowe.

4. Po skonfigurowaniu parametrów wybierz lokalizację projektu, a następnie kliknij pozycję **Utwórz**.

Visual Studio dla komputerów Mac tworzy projekt .NET Standard z uwzględnioną funkcją domyślną. Zawiera on również NuGet do różnych pakietów **AzureWebJobs,** a takżeNewtonsoft.Js **pakietu.**

![Visual Studio dla komputerów Mac wyświetlający zupełnie nową funkcję platformy Azure z szablonu](media/azure-functions-newproj.png)

Nowy projekt zawiera następujące pliki:

* **your-function-name.cs** — ta klasa zawiera kod dla wybranej funkcji. Zawiera ona atrybut **FunctionName** z nazwą funkcji i atrybut wyzwalacza, który określa, co wyzwala funkcję (np. żądanie HTTP). Aby uzyskać więcej informacji na temat metody funkcji, zapoznaj się z [artykułem Azure Functions języka C# dla deweloperów.](/azure/azure-functions/functions-dotnet-class-library)
* **host.js—** w tym pliku opisano globalne opcje konfiguracji hosta usługi Functions. Aby uzyskać przykładowy plik i informacje na temat dostępnych ustawień dla tego pliku, zobaczhost.js[ informacje dotyczące](/azure/azure-functions/functions-host-json)Azure Functions .
* **local.settings.js—** ten plik zawiera wszystkie ustawienia uruchamiania funkcji lokalnie. Te ustawienia są używane przez Azure Functions Core Tools. Aby uzyskać więcej informacji, zobacz [plik ustawień lokalnych](/azure/azure-functions/functions-run-local#local-settings-file) w Azure Functions Core Tools artykułu.

Teraz, po utworzeniu nowego projektu usługi Azure Functions w programie Visual Studio dla komputerów Mac, możesz przetestować domyślną funkcję wyzwalaną przez protokół HTTP z komputera lokalnego.

## <a name="testing-the-function-locally"></a>Testowanie funkcji lokalnie

Dzięki Azure Functions w Visual Studio dla komputerów Mac można przetestować i debugować funkcję na lokalnym komputerze dewelopera.

1. Aby przetestować funkcję lokalnie, naciśnij **przycisk Uruchom** w Visual Studio dla komputerów Mac:

    ![Przycisk Rozpocznij debugowanie w programie Visual Studio dla komputerów Mac](media/azure-functions-run.png)

1. Uruchomienie projektu rozpoczyna lokalne debugowanie funkcji platformy Azure i otwiera nowe okno terminalu, jak pokazano na poniższej ilustracji:

    ![okno terminalu z wyświetlaniem danych wyjściowych funkcji](media/azure-functions-terminal.png)

    Skopiuj adres URL z danych wyjściowych.

3. Wklej adres URL żądania HTTP w pasku adresu przeglądarki. Dodaj ciąg zapytania `?name=<yourname>` na końcu adresu URL i wykonaj żądanie. Na poniższej ilustracji przedstawiono odpowiedź w przeglądarce na lokalne żądanie GET zwrócone przez funkcję:

    ![żądanie http w przeglądarce](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Dodawanie kolejnej funkcji do projektu

Szablony funkcji umożliwiają szybkie tworzenie nowych funkcji przy użyciu najczęściej stosowanych wyzwalaczy i szablonów. Aby utworzyć inny typ funkcji, wykonaj następujące czynności:

1. Aby dodać nową funkcję, kliknij prawym przyciskiem myszy nazwę projektu i wybierz polecenie Dodaj > **Dodaj funkcję...**:

    ![akcja kontekstowa dodawania nowej funkcji](media/azure-functions-addnew.png)

2. W **oknie dialogowym Nowa funkcja** platformy Azure wybierz funkcję, która jest ci potrzebne:

    ![okno dialogowe nowej funkcji platformy Azure](media/azure-functions-image4.png)

    Lista szablonów funkcji platformy Azure jest dostępna w sekcji [Dostępne szablony](#available-function-templates) funkcji.

Przy użyciu powyższej procedury można dodać więcej funkcji do projektu aplikacji funkcji. Każda funkcja w projekcie może mieć inny wyzwalacz, ale funkcja musi mieć dokładnie jeden wyzwalacz. Aby uzyskać więcej informacji, [zobacz Azure Functions wyzwalaczy i powiązań](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publikowanie na platformie Azure

1. Kliknij prawym przyciskiem myszy nazwę projektu i wybierz polecenie Publish **> Publish to Azure**: Context menu with Publish > Publish to  ![ Azure... wyróżniona opcja](media/azure-functions-image5.png)
2. Jeśli konto platformy Azure zostało już połączone z usługą Visual Studio dla komputerów Mac zostanie wyświetlona lista dostępnych usług aplikacji. Jeśli nie zalogowano się, zostanie wyświetlony monit o jej zalogowanie.
3. W **oknie dialogowym Azure App Service** publikowania można wybrać istniejącą usługę aplikacji lub utworzyć nową, klikając pozycję **Nowy.**
4. W **oknie dialogowym App Service** nową grupę zasobów wprowadź ustawienia: Nowy App Service, z polami nazwy usługi, subskrypcji, grupy zasobów  ![ i planu usługi.](media/azure-functions-image7.png)

    |Ustawienie  |Opis  |
    |---------|---------|
    |**Nazwa usługi App Service**|Globalnie unikatowa nazwa identyfikująca nową aplikację funkcji.|
    |**Subskrypcja**|Subskrypcja platformy Azure, która ma być używana.|
    |**[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)**|Nazwa grupy zasobów, w której ma zostać utworzona aplikacja funkcji. Wybierz, **+** aby utworzyć nową grupę zasobów.|
    |**[Plan usługi](/azure/azure-functions/functions-scale)**|Wybierz istniejący plan lub utwórz plan niestandardowy. Wybierz lokalizację w regionie w pobliżu ciebie lub w pobliżu innych usług, do których Twoje funkcje mają dostęp.|

5. Kliknij **przycisk Dalej,** aby utworzyć konto magazynu. Środowisko uruchomieniowe usługi Functions wymaga konta magazynu platformy Azure. Kliknij **pozycję** Niestandardowy, aby utworzyć konto magazynu ogólnego przeznaczenia, lub użyj istniejącego konta:

    ![Nowe App Service dialogowe z monitem o nazwę konta magazynu.](media/azure-functions-image8.png)

6. Kliknij przycisk **Utwórz**, aby utworzyć aplikację funkcji i powiązane zasoby na platformie Azure przy użyciu tych ustawień i wdrożyć kod projektu funkcji.

7. Podczas publikowania może zostać wyświetlone okno dialogowe z monitem o zaktualizowanie wersji funkcji na platformie Azure. Kliknij **przycisk Tak:**

    ![Monituj o pytanie "Aktualizuj ustawienia aplikacji platformy Azure, aby dopasować je do lokalnej wersji funkcji?". z opcjami Tak i Nie.](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Ustawienia aplikacji funkcji

Wszystkie ustawienia dodane w local.settings.jsmuszą zostać również dodane do aplikacji funkcji na platformie Azure. Te ustawienia nie są przekazywane automatycznie podczas publikowania projektu.

Aby uzyskać dostęp do ustawień aplikacji, przejdź do strony Azure Portal stronie [https://ms.portal.azure.com/](https://ms.portal.azure.com/) . W **obszarze Aplikacje funkcji** wybierz pozycję Aplikacje **funkcji** i wyróżnij nazwę funkcji:

![menu usługi Azure Functions](media/azure-functions-image9.png)

Na karcie **Przegląd wybierz** pozycję Ustawienia **aplikacji w** obszarze **Skonfigurowane funkcje:**

![Over tab of azure function (Na karcie funkcji platformy Azure)](media/azure-functions-image10.png)

W tym miejscu możesz ustawić Ustawienia dla aplikacji funkcji, w której możesz dodać nowe ustawienia aplikacji lub zmodyfikować istniejące:

![obszar ustawień aplikacji Azure Portal](media/azure-functions-image11.png)

Jednym z ważnych ustawień, które może być konieczne, jest `FUNCTIONS_EXTENSION_VERSION` . Podczas publikowania z Visual Studio dla komputerów Mac należy ustawić tę wartość na **beta**.

## <a name="available-function-templates"></a>Dostępne szablony funkcji

- **GitHub Wyzwalacz** — odpowiadanie na zdarzenia występujące w repozytoriach GitHub użytkownika. Aby uzyskać więcej informacji, zobacz [artykuł Azure Functions na GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
  - GitHub komentarza — ta funkcja zostanie uruchamiana po otrzymaniu GitHub webhook dla problemu lub żądania ściągnnięcia i dodano komentarz.
  - GitHub WebHook — ta funkcja zostanie uruchamiana po otrzymaniu GitHub webhook.

- **HTTP** — wyzwala wykonywanie kodu przy użyciu żądania HTTP. Istnieją jawne szablony dla następujących wyzwalaczy HTTP:
  - Wyzwalacz HTTP
  - Http GET CRUD
  - Http POST CRUD
  - Wyzwalacz HTTP z parametrami

- **Czasomierz** — wykonuje oczyszczanie lub inne zadania wsadowe zgodnie ze wstępnie zdefiniowanym harmonogramem. Ten szablon przyjmuje dwa pola: nazwę i harmonogram, czyli sześć pól wyrażenia CRON. Aby uzyskać więcej informacji, zobacz [artykuł Azure Functions na czas](/azure/azure-functions/functions-create-scheduled-function)

- **Wyzwalacz kolejki** — jest to funkcja, która będzie odpowiadać na komunikaty przychodzące do kolejki Storage Azure. Oprócz nazwy funkcji ten szablon przyjmuje ścieżkę **(nazwę** kolejki, z której będzie odczytywany komunikat) i połączenie konta magazynu **(nazwę** ustawienia aplikacji zawierającego ciąg połączenia konta magazynu). Aby uzyskać więcej informacji, zobacz [artykuł Azure Functions usługi Queue Storage](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Wyzwalacz obiektu blob** — przetwarzanie Storage Azure po dodaniu obiektów blob do kontenera. Oprócz nazwy funkcji ten szablon przyjmuje również właściwość ścieżki i połączenia. Właściwość path jest ścieżką w ramach konta magazynu, którą będzie monitorować wyzwalacz. Konto połączenia to nazwa ustawienia aplikacji zawierającego ciąg połączenia konta magazynu. Aby uzyskać więcej informacji, zobacz [artykuł Azure Functions blob Storage blob](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Ogólny webhook —** jest to prosta funkcja, która będzie uruchamiana za każdym razem, gdy odbierze żądanie z dowolnej usługi obsługującej webhook. Aby uzyskać więcej informacji, zobacz [artykuł Azure Functions na temat ogólnych webhook.](/azure/azure-functions/functions-create-generic-webhook-triggered-function)

- **Orkiestracji funkcji trwałych** — Durable Functions umożliwia pisanie funkcji stanowych w środowisku bez serwera. Rozszerzenie zarządza stanem, punktami kontrolnymi i ponownym uruchamianiem. Aby uzyskać więcej informacji, zobacz Azure Functions przewodników dotyczących [funkcji trwałych.](/azure/azure-functions/durable-functions-overview)

- **Zmiana rozmiaru obrazów** — ta funkcja tworzy obrazy o zmienionym rozmiarze za każdym razem, gdy obiekt blob jest dodawany do kontenera. Szablon przyjmuje ścieżkę i ciąg połączenia dla wyzwalacza, małe dane wyjściowe obrazu i średnie dane wyjściowe obrazu.

- **Token SAS** — ta funkcja generuje token SAS dla danego kontenera usługi Azure Storage nazwę obiektu blob. Oprócz nazwy funkcji ten szablon przyjmuje również właściwość ścieżki i połączenia. Właściwość path jest ścieżką w ramach konta magazynu, którą będzie monitorować wyzwalacz. Konto połączenia to nazwa ustawienia aplikacji zawierającego ciąg połączenia konta magazynu. Należy **również** ustawić prawa dostępu. Poziom autoryzacji określa, czy funkcja wymaga klucza interfejsu API i którego klucza użyć; Funkcja używa klucza funkcji; Administrator używa Twojego klucza dostępu do konta. Aby uzyskać więcej informacji, zobacz przykład funkcji platformy Azure w języku C# służącej [do generowania tokenów SAS.](https://github.com/Azure-Samples/functions-dotnet-sas-token/)
