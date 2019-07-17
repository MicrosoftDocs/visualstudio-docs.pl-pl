---
title: Debugowanie aplikacji w lokalnym kontenerze platformy Docker | Dokumentacja firmy Microsoft
description: Dowiedz się, jak zmodyfikować aplikację, która jest uruchomiona w lokalnym kontenerze Docker, odśwież kontener za pomocą edytowania i odświeżania, a następnie ustaw, debugowanie punktów przerwania.
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 03/05/2019
ms.author: ghogen
ms.technology: vs-azure
ms.openlocfilehash: 70f78f1e7ed05f771e188fe922fef769a38799f9
ms.sourcegitcommit: f369ff7e84b0216f01570a486c7be80ca6d0e61a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68250439"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Debugowanie aplikacji w lokalnym kontenerze Docker

Program Visual Studio zapewnia spójny sposób programowania w kontenerze platformy Docker i zweryfikowania aplikacji w środowisku lokalnym. Nie trzeba ponownie uruchomić kontener każdorazowo, gdy wprowadzeniu zmiana w kodzie.

W tym artykule przedstawiono sposób użycia funkcji edytowania i odświeżania w programie Visual Studio, aby uruchomić aplikację internetową platformy ASP.NET Core w lokalnym kontenerze Docker, wprowadzić zmiany, a następnie odśwież przeglądarkę, aby zobaczyć zmiany. W tym artykule przedstawiono również sposób ustawiania punktów przerwania do debugowania.

## <a name="prerequisites"></a>Wymagania wstępne

Aby debugować aplikacje w lokalnym kontenerze Docker, muszą być zainstalowane następujące narzędzia:

::: moniker range="vs-2017"

* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowanym obciążeniem programowania dla sieci Web

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem programowania dla sieci Web

::: moniker-end

Do uruchamiania kontenerów platformy Docker lokalnie, konieczne jest posiadanie lokalnej klienta platformy Docker. Możesz użyć [przybornika Docker](https://www.docker.com/products/docker-toolbox), które wymagają funkcji Hyper-V można wyłączyć. Możesz również użyć [Docker for Windows](https://www.docker.com/get-docker), które korzysta z funkcji Hyper-V i wymaga systemu Windows 10. Jeśli używasz przybornika platformy Docker, należy skonfigurować klienta platformy Docker.

Kontenery platformy docker są dostępne dla projektów .NET Framework i .NET Core. Przyjrzyjmy się dwa przykłady. Najpierw przyjrzymy się aplikację sieci web platformy .NET Core. Następnie przyjrzymy się aplikacja konsoli .NET Framework.

## <a name="create-a-web-app"></a>tworzenie aplikacji internetowej

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[! OBEJMUJĄ [utworzyć aspnet5-aplikacji-2019 r](../azure/includes/vs-2019/create-aspnet5-app-2019.md)
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Edytuj kod i odświeżanie

Możesz szybko iterować zmiany, możesz uruchomić aplikację w kontenerze. Następnie należy kontynuować wprowadzanie zmian, ich wyświetlania, jak w przypadku usługi IIS Express.

1. Ustaw **konfiguracji rozwiązania** do **debugowania**. Naciśnij klawisze Ctrl + F5, aby skompilować obraz platformy Docker i uruchomić go lokalnie.

    Po utworzeniu obrazu kontenera i uruchomiona w kontenerze platformy Docker, Visual Studio uruchamia aplikację sieci web w domyślnej przeglądarce.

2. Przejdź do *indeksu* strony. Wybierzemy zmiany na tej stronie.
3. Wróć do programu Visual Studio i Otwórz *Index.cshtml*.
4. Dodaj następującą zawartość HTML do końca pliku, a następnie zapisz zmiany.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

5. W oknie danych wyjściowych po zakończeniu kompilacji platformy .NET, i zobaczysz następujące wiersze, wróć do przeglądarki i Odśwież stronę:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Zmiany zostały zastosowane!

### <a name="debug-with-breakpoints"></a>Debugować z punktami przerwania

Często zmiany wymagają dalszych inspekcji. Można użyć funkcji debugowania programu Visual Studio dla tego zadania.

1. W programie Visual Studio, otwórz *Index.cshtml.cs*.
2. Zastąp zawartość `OnGet` metoda następującym kodem:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Po lewej stronie wiersza kodu należy ustawić punkt przerwania.
4. Aby rozpocząć debugowanie i trafiony punkt przerwania, naciśnij klawisz F5.
5. Przełącz się do programu Visual Studio, aby wyświetlić punkt przerwania. Sprawdź wartości.

   ![Punkt przerwania](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Tworzenie aplikacji konsoli .NET Framework

Gdy używasz projektów aplikacji konsoli .NET Framework, opcję, aby dodać obsługę platformy Docker bez orchestration nie jest obsługiwane. Nadal można użyć poniższej procedury, nawet wtedy, gdy używasz tylko jeden projekt platformy Docker.

1. Utwórz nowy projekt aplikacji platformy .NET Framework konsoli.
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Dodaj** > **Obsługa aranżacji kontenerów**.  W oknie dialogowym wybierz **narzędzia Docker Compose**. Plik Dockerfile zostanie dodany do projektu i dodaniu projektu narzędzia Docker Compose za pomocą plików skojarzone pomocy technicznej.

### <a name="debug-with-breakpoints"></a>Debugować z punktami przerwania

1. W Eksploratorze rozwiązań Otwórz *Program.cs*.
2. Zastąp zawartość `Main` metoda następującym kodem:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Ustaw punkt przerwania na lewo od linii kodu.
4. Naciśnij klawisz F5, aby rozpocząć debugowanie i trafiony punkt przerwania.
5. Przełącz się do programu Visual Studio, aby wyświetlić punkt przerwania i sprawdzić wartości.

   ![Punkt przerwania](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Ponowne użycie kontenerów

Podczas cyklu rozwoju Visual Studio ponownie kompiluje tylko obrazy kontenera i samego kontenera po zmianie pliku Dockerfile. Jeśli nie zmienisz plik Dockerfile, Visual Studio ponownie używa kontenerów z wcześniejszych uruchamiania.

Jeśli ręcznie zmodyfikowano kontenera i chcesz ponownie uruchom za pomocą obrazu kontenera czystą użycia **kompilacji** > **czysty** polecenia w programie Visual Studio, a następnie Skompiluj w zwykły sposób.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Dowiedz się, jak [Rozwiązywanie problemów z programowania Visual Studio Docker](troubleshooting-docker-errors.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Więcej informacji na temat platformy Docker przy użyciu programu Visual Studio, Windows i platformy Azure

* Dowiedz się więcej o [programowania kontenerów przy użyciu programu Visual Studio](/visualstudio/containers).
* Aby skompilować i wdrożyć kontener platformy Docker, zobacz [Integracja z platformą Docker dla usługi Azure potoków](https://aka.ms/dockertoolsforvsts).
* Dla indeksu artykułów systemu Windows Server i serwer Nano Server, zobacz [informacje o kontenerze Windows](https://aka.ms/containers).
* Dowiedz się więcej o [usługi Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) i przejrzyj [dokumentacji usługi Azure Kubernetes Service](/azure/aks).
