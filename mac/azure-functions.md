---
title: Wprowadzenie do usługi Azure Functions
description: Korzystanie z usługi Azure Functions w Visual Studio dla komputerów Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: ef59a45bd3dd5b3ab2f3e5219d6674c8e7b095e2
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108075"
---
# <a name="introduction-to-azure-functions"></a>Wprowadzenie do usługi Azure Functions

Usługa Azure Functions to sposób tworzenia i uruchamiania fragmentów kodu opartych na zdarzeniach — w chmurze, bez konieczności jawnego udostępniania infrastruktury ani zarządzania nią. Aby uzyskać więcej informacji na temat Azure Functions, zobacz [dokumentację Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Wymagania

Narzędzia usługi Azure Functions są zawarte w **Visual Studio dla komputerów Mac 7,5** i nowszych.

Aby tworzyć i wdrażać funkcje, należy również uzyskać subskrypcję platformy Azure, która jest dostępna [https://azure.com/free](https://azure.com/free)bezpłatnie z programu.

## <a name="creating-your-first-azure-functions-project"></a>Tworzenie pierwszego projektu Azure Functions

1. W Visual Studio dla komputerów Mac wybierz pozycję **plik > nowe rozwiązanie**.
2. W oknie dialogowym Nowy projekt wybierz szablon Azure Functions w obszarze **Cloud > ogólne** , a następnie kliknij przycisk **dalej**:

    ![Okno dialogowe Nowy projekt z opcją Azure Functions](media/azure-functions-image1.png)

3. Wybierz początkowy szablon Azure Functions, którego chcesz użyć, wprowadź nazwę funkcji, a następnie kliknij przycisk **dalej**.

    ![Okno dialogowe Nowy projekt z szablonami usługi Azure Functions](media/azure-functions-image2.png)

    > [!TIP]
    > Chociaż powiązane Azure Functions środowisko uruchomieniowe i szablony (CLI) są jak najprawdopodobniej aktualne, są one nieaktualne. Podczas tworzenia nowego projektu funkcji program Visual Studio dla komputerów Mac sprawdzi dostępność aktualizacji interfejsu wiersza polecenia i wyświetli powiadomienie, jak pokazano na poniższej ilustracji. Wystarczy kliknąć przycisk, aby pobrać zaktualizowane szablony.
    > ![Dostępne jest okno dialogowe Nowy projekt pokazujące aktualizacje usługi Azure Functions](media/azure-functions-update.png)

    W zależności od wybranego typu funkcji Następna strona wyświetli monit o podanie szczegółowych informacji, takich jak prawa dostępu, jak pokazano na poniższej ilustracji:

    ![Okno dialogowe Nowy projekt z dodatkową opcją](media/azure-functions-image3.png)

    Aby uzyskać więcej informacji na temat różnych typów szablonów Azure Functions i właściwości powiązań wymaganych do skonfigurowania poszczególnych szablonów, zobacz sekcję [dostępne szablony funkcji](#available-function-templates) . W tym przykładzie korzystamy z wyzwalacza http z prawami dostępu ustawionymi jako anonimowe.

4. Po ustawieniu parametrów wybierz lokalizację projektu i kliknij przycisk **Utwórz**.

Visual Studio dla komputerów Mac tworzy projekt .NET Standard z dołączoną funkcją domyślną. Zawiera również odwołania NuGet do różnych pakietów **AzureWebJobs** , a także pakiet **Newtonsoft. JSON** .

![Edytor Visual Studio dla komputerów Mac wyświetlający zupełnie nową funkcję platformy Azure z szablonu](media/azure-functions-newproj.png)

Nowy projekt zawiera następujące pliki:

* **Your-Function-Name.cs** — Ta klasa zawiera kod standardowy dla wybranej funkcji. Zawiera atrybut **FunctionName** z nazwą funkcji i atrybut wyzwalacza, który określa, co wyzwala funkcja (np. żądanie HTTP). Aby uzyskać więcej informacji o metodzie funkcji, zapoznaj się z artykułem dotyczącym [dokumentacji dla deweloperów Azure Functions C# ](/azure/azure-functions/functions-dotnet-class-library) .
* **host. JSON** — ten plik zawiera opis globalnych opcji konfiguracji dla hosta usługi Functions. Przykładowy plik i informacje dotyczące dostępnych ustawień dla tego pliku można znaleźć w [dokumentacji pliku host. JSON dla Azure Functions](/azure/azure-functions/functions-host-json).
* **Local. Settings. JSON** — ten plik zawiera wszystkie ustawienia dla uruchomionych funkcji lokalnie. Te ustawienia są używane przez Azure Functions Core Tools. Aby uzyskać więcej informacji, zobacz [plik ustawień lokalnych](/azure/azure-functions/functions-run-local#local-settings-file) w artykule Azure Functions Core Tools.

Po utworzeniu nowego projektu Azure Functions w Visual Studio dla komputerów Mac można przetestować domyślną funkcję wyzwalaną przez protokół HTTP na komputerze lokalnym.

## <a name="testing-the-function-locally"></a>Lokalne testowanie funkcji

Dzięki obsłudze Azure Functions w Visual Studio dla komputerów Mac można testować i debugować funkcję na lokalnym komputerze deweloperskim.

1. Aby przetestować funkcję lokalnie, naciśnij przycisk **Run (Uruchom** ) w Visual Studio dla komputerów Mac:

    ![Przycisk Rozpocznij debugowanie w programie Visual Studio dla komputerów Mac](media/azure-functions-run.png)

1. Uruchomienie projektu uruchamia lokalne debugowanie w usłudze Azure Function i otwiera nowe okno terminalu, jak pokazano na poniższej ilustracji:

    ![okno terminalu przedstawiające dane wyjściowe funkcji](media/azure-functions-terminal.png)

    Skopiuj adres URL z danych wyjściowych.

3. Wklej adres URL żądania HTTP na pasku adresu przeglądarki. Dodaj ciąg `?name=<yourname>` zapytania na końcu adresu URL i wykonaj żądanie. Na poniższej ilustracji przedstawiono odpowiedź w przeglądarce do lokalnego żądania GET zwróconego przez funkcję:

    ![żądanie HTTP w przeglądarce](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Dodawanie innej funkcji do projektu

Szablony funkcji umożliwiają szybkie tworzenie nowych funkcji przy użyciu najczęściej stosowanych wyzwalaczy i szablonów. Aby utworzyć inny typ funkcji, wykonaj następujące czynności:

1. Aby dodać nową funkcję, kliknij prawym przyciskiem myszy nazwę projektu i wybierz polecenie **dodaj > Dodaj funkcję...** :

    ![Akcja kontekstowa dodawania nowej funkcji](media/azure-functions-addnew.png)

2. W oknie dialogowym **Nowa funkcja platformy Azure** wybierz wymaganą funkcję:

    ![nowe okno dialogowe funkcji platformy Azure](media/azure-functions-image4.png)

    Lista szablonów funkcji platformy Azure znajduje się w sekcji [dostępne szablony funkcji](#available-function-templates) .

Korzystając z powyższej procedury, można dodać więcej funkcji do projektu aplikacji funkcji. Każda funkcja w projekcie może mieć inny wyzwalacz, ale funkcja musi mieć dokładnie jeden wyzwalacz. Aby uzyskać więcej informacji, zobacz temat [Azure Functions wyzwalacze i koncepcje powiązań](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publikowanie na platformie Azure

1. Kliknij prawym przyciskiem myszy nazwę projektu i wybierz pozycję **publikuj > Opublikuj na platformie Azure**:  ![Opcja menu Publikuj w systemie Azure](media/azure-functions-image5.png)
2. Jeśli masz już połączenie z kontem platformy Azure w celu Visual Studio dla komputerów Mac zostanie wyświetlona lista dostępnych usług App Services. Jeśli użytkownik nie zalogował się, zostanie wyświetlony odpowiedni monit.
3. W oknie dialogowym **Publikowanie w Azure App Service** możesz wybrać istniejącą usługę App Service lub utworzyć nową, klikając przycisk **Nowy**.
4. W oknie dialogowym **Tworzenie nowego App Service** wprowadź ustawienia:  ![Opcja menu Publikuj w systemie Azure](media/azure-functions-image7.png)

    |Ustawienie  |Opis  |
    |---------|---------|
    |**Nazwa App Service**|Globalnie unikatowa nazwa identyfikująca nową aplikację funkcji.|
    |**Subskrypcja**|Subskrypcja platformy Azure do użycia.|
    |**[Grupa zasobów](/azure/azure-resource-manager/resource-group-overview)**|Nazwa grupy zasobów, w której ma zostać utworzona aplikacja funkcji. Wybierz **+** opcję utworzenia nowej grupy zasobów.|
    |**[Plan usługi](/azure/azure-functions/functions-scale)**|Wybierz istniejący plan lub Utwórz plan niestandardowy. Wybierz lokalizację w regionie blisko siebie lub w niemal innych usługach, do których dostęp ma funkcja.|

5. Kliknij przycisk **dalej** , aby utworzyć konto magazynu. Konto usługi Azure Storage jest wymagane przez środowisko uruchomieniowe funkcji. Kliknij pozycję **niestandardowy** , aby utworzyć konto magazynu ogólnego przeznaczenia, lub Użyj istniejącego:

    ![Opcja menu Publikuj w systemie Azure](media/azure-functions-image8.png)

6. Kliknij przycisk **Utwórz** , aby utworzyć aplikację funkcji i powiązane zasoby na platformie Azure z tymi ustawieniami i wdrożyć kod projektu funkcji.

7. Podczas publikowania może pojawić się okno dialogowe z informacją o tym, jak zaktualizować wersję funkcji na platformie Azure. Kliknij przycisk **tak**:

    ![Opcja menu Publikuj w systemie Azure](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Ustawienia aplikacji funkcji

Wszystkie ustawienia dodane w pliku Local. Settings. JSON należy również dodać do aplikacji funkcji na platformie Azure. Te ustawienia nie są przekazywane automatycznie po opublikowaniu projektu.

Aby uzyskać dostęp do ustawień aplikacji, przejdź do Azure Portal pod [https://ms.portal.azure.com/](https://ms.portal.azure.com/)adresem. W obszarze **aplikacje funkcje**wybierz pozycję **aplikacje funkcji** i wyróżnij nazwę funkcji:

![menu usługi Azure Functions](media/azure-functions-image9.png)

Na karcie **Przegląd** wybierz pozycję **Ustawienia aplikacji** w obszarze **skonfigurowane funkcje**:

![Za pośrednictwem karty usługi Azure Functions](media/azure-functions-image10.png)

W tym miejscu możesz ustawić ustawienia aplikacji dla aplikacji funkcji, w której można dodać nowe ustawienia aplikacji lub zmodyfikować istniejące:

![Obszar ustawień aplikacji Azure Portal](media/azure-functions-image11.png)

Jednym z ważnych ustawień może być konieczne ustawienie wartości `FUNCTIONS_EXTENSION_VERSION`. W przypadku publikowania z Visual Studio dla komputerów Mac należy ustawić wartość **beta**.

## <a name="available-function-templates"></a>Dostępne szablony funkcji

- **Wyzwalacz usługi GitHub** — odpowiadanie na zdarzenia występujące w repozytoriach usługi GitHub. Aby uzyskać więcej informacji, zobacz [artykuł Azure Functions w witrynie GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
  - Komentarz w witrynie GitHub — ta funkcja zostanie uruchomiona, gdy odbierze element webhook usługi GitHub dla problemu lub żądania ściągnięcia i doda komentarz.
  - Element webhook usługi GitHub — ta funkcja zostanie uruchomiona, gdy odbierze element webhook usługi GitHub.

- **Http** — wyzwalanie wykonywania kodu przy użyciu żądania HTTP. Istnieją jawne szablony dla następujących wyzwalaczy HTTP:
  - Wyzwalacz http
  - HTTP GET CRUD
  - HTTP POST CRUD
  - Wyzwalacz http z parametrami

- **Timer** — wykonaj oczyszczanie lub inne zadania wsadowe zgodnie ze wstępnie zdefiniowanym harmonogramem. Ten szablon przyjmuje dwa pola: nazwę i harmonogram, czyli sześć wyrażeń firmy cronus. Aby uzyskać więcej informacji, zobacz [artykuł dotyczący usługi Azure Functions w czasie](/azure/azure-functions/functions-create-scheduled-function)

- **Wyzwalacz kolejki** — jest to funkcja, która będzie odpowiadać na komunikaty, gdy docierają one do kolejki usługi Azure Storage. Oprócz nazwy funkcji ten szablon przyjmuje **ścieżkę** (nazwę kolejki, z której zostanie odczytany komunikat) i **połączenie** konta magazynu (nazwę aplikacji zawierającą parametry połączenia konta magazynu). Aby uzyskać więcej informacji, zobacz [artykuł dotyczący usługi Azure Functions w queue storage](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Wyzwalacz obiektów BLOB** — przetwarzanie obiektów BLOB usługi Azure Storage po ich dodaniu do kontenera. Oprócz nazwy funkcji ten szablon przyjmuje również właściwość Path i Connection. Właściwość Path jest ścieżką w ramach konta magazynu, który będzie monitorowany przez wyzwalacz. Konto połączenia to nazwa ustawienia aplikacji zawierającego parametry połączenia konta magazynu. Aby uzyskać więcej informacji, zobacz [artykuł dotyczący usługi Azure functions BLOB Storage](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Ogólny element webhook** — prosta funkcja, która będzie uruchamiana za każdym razem, gdy odbierze żądanie od dowolnej usługi obsługującej elementy webhook. Aby uzyskać więcej informacji, zobacz [artykuł dotyczący usługi Azure Functions w ogólnych elementach webhook](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Aranżacja funkcji trwałych** — Durable Functions pozwala pisać funkcje stanowe w środowisku bezserwerowym. Rozszerzenie zarządza stanem, punktami kontrolnymi i ponownymi uruchomieniami. Aby uzyskać więcej informacji, zobacz Przewodniki usługi Azure Functions dotyczący [trwałych funkcji](/azure/azure-functions/durable-functions-overview).

- Wskaźnik **rozmiaru obrazu** — ta funkcja tworzy obrazy o zmienionym rozmiarze za każdym razem, gdy obiekt BLOB zostanie dodany do kontenera. Szablon przyjmuje ścieżkę i parametry połączenia dla wyzwalacza, niewielką wartość wyjściową obrazu oraz średnią wartość wyjściową obrazu.

- **Token sygnatury** dostępu współdzielonego — ta funkcja generuje token sygnatury dostępu współdzielonego dla danego kontenera usługi Azure Storage i nazwy obiektu BLOB. Oprócz nazwy funkcji ten szablon przyjmuje również właściwość Path i Connection. Właściwość Path jest ścieżką w ramach konta magazynu, który będzie monitorowany przez wyzwalacz. Konto połączenia to nazwa ustawienia aplikacji zawierającego parametry połączenia konta magazynu. Należy również ustawić **prawa dostępu** . Poziom autoryzacji kontroluje, czy funkcja wymaga klucza interfejsu API i klucza, który ma być używany; Funkcja używa klucza funkcji; Administrator używa klucza głównego. Aby uzyskać więcej informacji, zobacz [ C# funkcja platformy Azure do generowania](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) przykładu tokenów SAS.
