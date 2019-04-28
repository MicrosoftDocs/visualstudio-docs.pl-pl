---
title: Wprowadzenie do usługi Azure Functions
description: Użycie usługi Azure functions w programie Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 8ceee693ee7b20e7045aa8bca4b895a0df383c80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62933604"
---
# <a name="introduction-to-azure-functions"></a>Wprowadzenie do usługi Azure Functions

Usługa Azure functions to sposób tworzenia i uruchamiania oparte na zdarzeniach fragmenty kodu — — funkcje — — w chmurze, bez konieczności jawnego przydzielania infrastruktury ani zarządzania tą infrastrukturą. Aby uzyskać więcej informacji na temat usługi Azure Functions, zobacz [dokumentacji usługi Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Wymagania

Narzędzia funkcji platformy Azure są objęte **programu Visual Studio dla komputerów Mac w wersji 7.5**.

Aby utworzyć i wdrożyć funkcje należy również subskrypcji platformy Azure, która jest dostępna bezpłatnie w [ https://azure.com/free ](https://azure.com/free).

## <a name="creating-your-first-azure-functions-project"></a>Tworzenie pierwszego projektu usługi Azure Functions

1. W programie Visual Studio dla komputerów Mac, wybierz **Plik > nowe rozwiązanie**.
2. Z poziomu okna dialogowego Nowy projekt, wybierz szablon usługi Azure Functions w ramach **chmura > Ogólne** i kliknij przycisk **dalej**:

    ![Okno dialogowe nowego projektu pokazujący opcję usługi Azure functions](media/azure-functions-image1.png)

3. Wybierz początkowy szablon usługi Azure Functions, którego chcesz użyć, wprowadź nazwę funkcji i kliknij przycisk **dalej**.

    ![Okno dialogowe nowego projektu przedstawiający szablony usługi Azure functions](media/azure-functions-image2.png)

    W zależności od typu funkcji, którą wybierzesz następnej strony wyświetli monit wprowadź szczegóły, takie jak prawa dostępu, jak pokazano na poniższej ilustracji:

    ![Okno dialogowe nowego projektu przedstawiający dodatkową opcję](media/azure-functions-image3.png)

    Aby uzyskać więcej informacji na temat różnych typów szablonów usługi Azure Functions i powiązania właściwości wymagane do skonfigurowania każdego szablonu, zobacz [szablonów dostępnych funkcji](#available-function-templates) sekcji. W tym przykładzie używamy wyzwalacza Http przy użyciu dostępu ustawionych uprawnień do anonimowych.

4. Po ustawieniu parametrów, wybierz lokalizację projektu i kliknij przycisk **Utwórz**.

Program Visual Studio for Mac tworzy projekt .NET Standard za pomocą domyślnej funkcji uwzględnione. Obejmuje również odwołania do NuGet z szeroką gamą **AzureWebJobs** pakietów, jak również **Newtonsoft.Json** pakietu.

![Program Visual Studio for Mac edytora wyświetlanie całkiem nowych funkcji platformy azure za pomocą szablonu](media/azure-functions-newproj.png)

Nowy projekt zawiera następujące pliki:

* **Twój name.cs funkcja** — ta klasa zawiera schematyczny kod służący do wybranej funkcji. Zawiera on **FunctionName** atrybutu o nazwie funkcji, a atrybut wyzwalacz, który określa, jakie wywołuje funkcję (np.) żądanie HTTP). Aby uzyskać więcej informacji na temat funkcji metody, zobacz [dokumentacja dla deweloperów usługi Azure Functions C#](/azure/azure-functions/functions-dotnet-class-library) artykułu.
* **Host.JSON** — w tym pliku opisano opcje konfiguracji globalnej dla hosta funkcji. Przykładowy plik i informacji na temat dostępnych ustawień dla tego pliku, zobacz [dokumentacja pliku host.JSON dla usługi Azure Functions](/azure/azure-functions/functions-host-json).
* **Local.Settings.JSON** — ten plik zawiera wszystkie ustawienia dla działających funkcji lokalnie. Te ustawienia są używane przez podstawowych narzędzi usługi Azure Functions. Aby uzyskać więcej informacji, zobacz [pliku ustawień lokalnych](/azure/azure-functions/functions-run-local#local-settings-file) w artykule podstawowych narzędzi usługi Azure Functions.

Teraz, po utworzeniu nowego projektu usługi Azure Functions w programie Visual Studio dla komputerów Mac, możesz przetestować się domyślnej funkcji wyzwalanej przez HTTP z komputera lokalnego.

## <a name="testing-the-function-locally"></a>Testowanie funkcji lokalnie

Dzięki obsłudze usługi Azure Functions w programie Visual Studio dla komputerów Mac może testowanie i debugowanie funkcji na lokalnym komputerze deweloperskim.

1. Aby przetestować funkcję lokalnie, naciśnij klawisz **Uruchom** przycisku w programie Visual Studio dla komputerów Mac:

    ![Rozpocznij debugowanie przycisku w programie visual studio dla komputerów mac](media/azure-functions-run.png)

1. Uruchamianie projektu uruchamia lokalne debugowanie funkcji platformy Azure i otwiera nowe okno terminalu, jak pokazano na poniższej ilustracji:

    ![dane wyjściowe funkcji przedstawiający okno terminalu](media/azure-functions-terminal.png)

    Skopiuj adres URL z danych wyjściowych.

3. Wklej adres URL żądania HTTP do paska adresu w przeglądarce. Dodaj ciąg zapytania `?name=<yourname>` na końcu adresu URL i wykonaj żądanie. Na poniższej ilustracji przedstawiono odpowiedzi w przeglądarce, aby lokalne żądanie GET zwróconą przez funkcję:

    ![żądania HTTP w przeglądarce](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Dodawanie innej funkcji do projektu

Szablony funkcji umożliwiają szybkie tworzenie nowych funkcji przy użyciu najczęściej stosowanych wyzwalaczy i szablonów. Aby utworzyć inny typ funkcji, wykonaj następujące czynności:

1. Aby dodać nową funkcję, kliknij prawym przyciskiem myszy nazwę projektu, a następnie wybierz **Dodaj > Dodaj funkcję...** :

    ![Akcja kontekstu do dodawania nowych funkcji](media/azure-functions-addnew.png)

2. Z **nowej funkcji platformy Azure** okno dialogowe, wybierz funkcję, potrzebujesz:

    ![okno dialogowe Nowy funkcji platformy azure](media/azure-functions-image4.png)

    Lista szablonów funkcji platformy Azure znajdują się w [szablonów dostępnych funkcji](#available-function-templates) sekcji.

Powyższej procedury można użyć, aby dodać więcej funkcji do projektu aplikacji funkcji. Każda funkcja w projekcie mogą mieć różne wyzwalacza, ale funkcja musi mieć dokładnie jeden wyzwalacz. Aby uzyskać więcej informacji, zobacz [pojęcia powiązania i Wyzwalacze usługi Azure Functions](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publikowanie na platformie Azure

1. Kliknij prawym przyciskiem myszy nazwę projektu, a następnie wybierz pozycję **Opublikuj > Opublikuj na platformie Azure**:  ![Publikowanie do opcji menu platformy azure](media/azure-functions-image5.png)
2. Jeśli już nawiązano subskrypcji platformy Azure konta programu Visual Studio dla komputerów Mac lista dostępnych aplikacji, które usługi są wyświetlane. Jeśli użytkownik nie zalogował się, zostanie wyświetlony monit Aby to zrobić.
3. Z **Publikuj w usłudze Azure App Service** okna dialogowego, można wybrać istniejącą usługę app lub Utwórz nowe, klikając **New**.
4. W **Tworzenie nowej usługi App Service** okno dialogowe, wprowadź ustawienia:  ![Publikowanie do opcji menu platformy azure](media/azure-functions-image7.png)

    |Ustawienie  |Opis  |
    |---------|---------|
    |**Nazwa usługi App Service**|Unikatowa nazwa identyfikująca nową aplikację funkcji.|
    |**Subskrypcja**|Subskrypcja platformy Azure do użycia.|
    |**[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)**|Nazwa grupy zasobów, w której chcesz utworzyć aplikację funkcji. Wybierz **+** do tworzenia nowej grupy zasobów.|
    |**[Plan usługi](/azure/azure-functions/functions-scale)**|Wybierz istniejący plan lub utworzyć niestandardowy plan. Wybierz lokalizację w regionie blisko Ciebie lub w pobliżu innych usług, dostęp do usługi functions.|

    > [!CAUTION]
    > Znajduje się błąd w 7.6 wersji programu Visual Studio dla komputerów Mac, który spowoduje, że publikowanie zakończona niepowodzeniem z powodu błędu inicjowania obsługi administracyjnej, jeśli próba utworzenia planu usług niestandardowych za pomocą **ceny** równa **zużycie**. Ten problem zostanie rozwiązany w następnej wersji usługi.

5. Kliknij przycisk **dalej** można utworzyć konta magazynu. Konto magazynu platformy Azure jest wymagane przez środowisko uruchomieniowe usługi Functions. Kliknij przycisk **niestandardowe** utworzyć konto magazynu ogólnego przeznaczenia lub użyj istniejącej:

    ![Publikowanie do opcji menu platformy azure](media/azure-functions-image8.png)

6. Kliknij przycisk **Utwórz** do tworzenia aplikacji funkcji i powiązanych zasobów na platformie Azure przy użyciu tych ustawień, a następnie wdrożyć kod projektu funkcji.

7. Może pojawić się prośba o okno dialogowe podczas publikowania, informujące o tym do "Aktualizacji funkcje wersji na platformie Azure". Kliknij przycisk **tak**:

    ![Publikowanie do opcji menu platformy azure](media/azure-functions-image12.png)

> [!CAUTION]
> W 7.6 wersji programu Visual Studio dla komputerów Mac znajduje się błąd gdzie `FUNCTIONS_EXTENSION_VERSION` nie jest poprawnie ustawiony na "beta", co oznacza, że funkcji może nie działać. Aby rozwiązać ten problem, przejdź do swojej [ustawień aplikacji funkcji](#function-app-settings) i ustaw `FUNCTIONS_EXTENSION_VERSION` od "-1" do "beta".

## <a name="function-app-settings"></a>Ustawienia aplikacji funkcji

Wszystkie ustawienia, które zostały dodane w local.settings.json należy również dodać do aplikacji funkcji na platformie Azure. Te ustawienia nie są ładowane automatycznie podczas publikowania projektu.

Aby uzyskać dostęp do ustawień aplikacji, przejdź do witryny azure portal pod [ https://ms.portal.azure.com/ ](https://ms.portal.azure.com/). W obszarze **aplikacje funkcji**, wybierz opcję **aplikacje funkcji** i wyróżnić swoją nazwę funkcji:

![Usługa Azure functions menu](media/azure-functions-image9.png)

Z **Przegląd** wybierz opcję **ustawienia aplikacji** w obszarze **skonfigurowane funkcje**:

![Na karcie funkcji platformy azure](media/azure-functions-image10.png)

W tym miejscu można ustawić ustawienia aplikacji dla aplikacji funkcji, w którym można dodawać nowych ustawień aplikacji lub zmodyfikuj istniejące:

![obszaru ustawień aplikacji w witrynie azure portal](media/azure-functions-image11.png)

Co ważne ustawienie może być konieczne ustawienie jest `FUNCTIONS_EXTENSION_VERSION`. Podczas publikowania z programu Visual Studio dla komputerów Mac, ta wartość powinna być równa **beta**.

## <a name="available-function-templates"></a>Szablony z dostępnych funkcji

- **Wyzwalacz usługi GitHub** — reagowanie na zdarzenia występujące w repozytoriach usługi GitHub. Aby uzyskać więcej informacji, zobacz [artykułu usługi Azure Functions w witrynie GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - Twórca komentarza usługi GitHub — ta funkcja będzie działać, gdy odbierze element webhook usługi GitHub dla problemu lub żądania ściągnięcia i doda komentarz.
    - Element WebHook usługi GitHub — będzie można uruchomić tej funkcji, gdy odbierze element webhook usługi GitHub.

- **HTTP** — wyzwalanie wykonywania kodu za pomocą żądania HTTP. Istnieją jawne szablonów dla następujących wyzwalaczy HTTP:
    - Wyzwalacz http
    - HTTP GET CRUD
    - CRUD POST protokołu HTTP
    - Wyzwalacz protokołu HTTP z parametrami

- **Czasomierz** — wykonywanie oczyszczania lub innych zadań wsadowych na ze wstępnie zdefiniowanym harmonogramem. Ten szablon ma dwa pola: nazwę i harmonogramu jest wyrażeniem CRON 6 pól. Aby uzyskać więcej informacji, zobacz [usługi Azure functions artykuł na czas](/azure/azure-functions/functions-create-scheduled-function)

- **Wyzwalacz kolejki** — jest to funkcja, która będzie odpowiadać na komunikaty przychodzące w kolejce usługi Azure Storage. Oprócz nazwy funkcji, ten szablon ma **ścieżki** (Nazwa kolejki, z której zostanie odczytany komunikat) i konto magazynu **połączenia** (Nazwa ustawienia aplikacji zawierającego magazynu Parametry połączenia dla konta). Aby uzyskać więcej informacji, zobacz [usługi Azure functions artykuł na usługi Queue Storage](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Obiekt blob wyzwalacza** — proces usługi Azure Storage, obiekty BLOB, gdy zostaną one dodane do kontenera. Oprócz nazwy funkcji ten szablon ma właściwości połączenia i ścieżki. Właściwość ścieżki jest ścieżka w ramach konta magazynu, którą będzie monitorował wyzwalacz. Konto połączenia jest nazwa ustawienia aplikacji zawierającego parametry połączenia konta magazynu. Aby uzyskać więcej informacji, zobacz [artykułu magazynu obiektów Blob usługi Azure functions](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Ogólny element WebHook** — jest to prostej funkcji, który będzie uruchamiany po każdym odebraniu żądania elementu z dowolnej usługi obsługującej takie elementy. Aby uzyskać więcej informacji, zobacz [usługi Azure functions artykuł na ogólny elementów webhook](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Trwałe funkcje aranżacji** — funkcje trwałe umożliwiają napisanie stanowych funkcji w środowisku bezserwerowym. Rozszerzenie zarządza stan, punkty kontrolne i ponowne uruchomienie dla Ciebie. Aby uzyskać więcej informacji, zapoznaj się z przewodnikami usługi Azure functions na [funkcje trwałe](/azure/azure-functions/durable-functions-overview).

- **Zmiany rozmiaru obrazu** — ta funkcja tworzy obrazy o zmienionym rozmiarze, po każdym dodaniu obiektu blob do kontenera. Szablon ma ścieżkę i parametry połączenia dla wyzwalacza, wyjściowy mały obraz i średnie obrazu wyjściowego.

- **Token sygnatury dostępu Współdzielonego** — ta funkcja generuje token SAS dla danego nazwy kontenera i obiektów blob usługi Azure Storage. Oprócz nazwy funkcji ten szablon ma właściwości połączenia i ścieżki. Właściwość ścieżki jest ścieżka w ramach konta magazynu, którą będzie monitorował wyzwalacz. Konto połączenia jest nazwa ustawienia aplikacji zawierającego parametry połączenia konta magazynu. **Prawa dostępu** również należy ustawić. Poziom autoryzacji określa, czy funkcja wymaga klucza interfejsu API i którego klucza należy użyć. Funkcja używa klucza funkcji; Administrator używa Twój klucz główny. Aby uzyskać więcej informacji, zobacz [Azure funkcja języka C# umożliwiająca Generowanie tokenów sygnatur dostępu Współdzielonego](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) próbki.