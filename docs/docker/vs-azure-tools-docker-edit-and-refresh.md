---
title: Debugowanie aplikacji w lokalnym kontenerze platformy Docker | Dokumentacja firmy Microsoft
description: Dowiedz się, jak zmodyfikować aplikację, która jest uruchomiona w lokalnym kontenerze Docker, odśwież kontener za pomocą edytowania i odświeżania i ustawiania punktów przerwania do debugowania
services: container-service
author: ghogen
manager: douge
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.service: multiple
ms.topic: article
ms.workload: multiple
ms.date: 09/11/2018
ms.author: ghogen
ms.openlocfilehash: 784fd5fd4459c77e757cc501ff5f62bce13d5282
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739846"
---
# <a name="debugging-apps-in-a-local-docker-container"></a>Debugowanie aplikacji w lokalnym kontenerze platformy Docker
## <a name="overview"></a>Omówienie
Program Visual Studio 2017 zapewnia spójny sposób programowania w kontenerze platformy Docker i zweryfikowania aplikacji w środowisku lokalnym.
Nie trzeba ponownie uruchomić kontener każdorazowo, gdy wprowadzeniu zmiana w kodzie.
W tym artykule pokazano, jak funkcja "Edytuj i Odśwież" Aby uruchomić aplikację sieci Web platformy ASP.NET Core w lokalnym kontenerze Docker, wprowadź niezbędne zmiany, a następnie odśwież przeglądarkę, aby zobaczyć zmiany.
W tym artykule przedstawiono również sposób ustawiania punktów przerwania do debugowania.

## <a name="prerequisites"></a>Wymagania wstępne
Muszą być zainstalowane następujące narzędzia.

* [Program Visual Studio 2017](https://www.visualstudio.com/downloads/) z zainstalowanym obciążeniem programowania dla sieci Web.

Do uruchamiania kontenerów platformy Docker lokalnie, należy klient lokalnej platformy docker.
Możesz użyć [przybornika Docker](https://www.docker.com/products/docker-toolbox), które wymagają funkcji Hyper-V można wyłączyć lub można użyć [Docker for Windows](https://www.docker.com/get-docker), które korzysta z funkcji Hyper-V i wymaga systemu Windows 10.

Jeśli używasz przybornika platformy Docker, konieczne będzie [Konfigurowanie klienta platformy Docker](vs-azure-tools-docker-setup.md)

## <a name="1-create-a-web-app"></a>1. tworzenie aplikacji internetowej
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]

## <a name="2-edit-your-code-and-refresh"></a>2. Edytuj kod i odświeżanie
Możesz szybko iterować zmiany, możesz uruchomić aplikację w kontenerze i kontynuować wprowadzanie zmian, ich wyświetlania, jak w przypadku usługi IIS Express.

1. Ustaw konfigurację rozwiązania `Debug` i naciśnij klawisz  **&lt;klawiszy CTRL + F5 >** Aby skompilować obraz platformy docker i uruchomić go lokalnie.

    Gdy obraz kontenera został skompilowany i jest uruchomiona w kontenerze platformy Docker, Visual Studio uruchamia aplikację sieci Web w domyślnej przeglądarce.
    Jeśli używasz przeglądarki Microsoft Edge lub w przeciwnym razie błędami, zobacz [Rozwiązywanie problemów](vs-azure-tools-docker-troubleshooting-docker-errors.md) sekcji.
2. Przejdź do strony informacje, czyli, gdzie zamierzamy nasze zmiany.
3. Wróć do programu Visual Studio i Otwórz `Views\Home\About.cshtml`.
4. Dodaj następującą zawartość HTML do końca pliku, a następnie zapisz zmiany.

    ```
    <h1>Hello from a Docker Container!</h1>
    ```
5. Wyświetlanie w oknie danych wyjściowych po ukończeniu kompilacji platformy .NET i wyświetlić te wiersze, wróć do przeglądarki, a następnie odśwież stronę informacje.

   ```
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down
   ```

6. Zmiany zostały zastosowane!

## <a name="3-debug-with-breakpoints"></a>3. Debugować z punktami przerwania
Często zmian będzie potrzebna jest dalsza inspekcji, korzystając z funkcji debugowania programu Visual Studio.

1. Wróć do programu Visual Studio i Otwórz `About.cshtml.cs`
2. Zastąp zawartość metody OnGet() następujących czynności:

   ```cs
       Message = "Your application description page from within a Container";
   ```

3. Ustaw punkt przerwania na lewo od linii kodu.
4. Trafienia  **&lt;F5 >** można rozpocząć debugowania.
5. Przejdź do strony informacje, aby trafić punkt przerwania.
6. Przełącz się do programu Visual Studio, aby wyświetlić punkt przerwania i sprawdzić wartość komunikatu.

   ![Punkt przerwania](media/vs-azure-tools-docker-edit-and-refresh/breakpoint.png)

## <a name="summary"></a>Podsumowanie
Dzięki obsłudze platformy Docker w programie Visual Studio 2017 możesz uzyskać wydajność pracy lokalnie, za pomocą realizmu produkcji rozwijających się w kontenerze platformy Docker.

## <a name="troubleshooting"></a>Rozwiązywanie problemów
[Rozwiązywanie problemów z programowanie Docker programu Visual Studio](vs-azure-tools-docker-troubleshooting-docker-errors.md)

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Więcej informacji na temat platformy Docker przy użyciu programu Visual Studio, Windows i platformy Azure
* [Tworzenie kontenerów za pomocą programu Visual Studio](/visualstudio/containers) — strona Centrum rozwoju kontenera
* [Integracja z platformą docker dla usługi Azure potoków](http://aka.ms/dockertoolsforvsts) — umożliwia tworzenie i wdrażanie kontenerów aparatu docker
* [Narzędzia aparatu docker dla programu Visual Studio Code](http://aka.ms/dockertoolsforvscode) — usługi w języka do edycji plików docker przy użyciu scenariuszy e2e mieszczących się
* [Informacje o kontenerze Windows](http://aka.ms/containers)— informacje o systemie Windows Server i serwera Nano Server
* [Usługa Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) - [dokumentacja usługi Azure Kubernetes Service](/azure/aks)

## <a name="various-docker-tools"></a>Różne narzędzia programu Docker
[Niektóre narzędzia docker doskonałe (blog Steve'a Lasker)](https://blogs.msdn.microsoft.com/stevelasker/2016/03/25/some-great-docker-tools/)

## <a name="good-articles"></a>Dobre artykuły
[Wprowadzenie do Mikrousług z NGINX](https://www.nginx.com/blog/introduction-to-microservices/)

## <a name="presentations"></a>Prezentacje
* [Steve Lasker: VS Live Las Vegas 2016 - e2e platformy Docker](https://github.com/SteveLasker/Presentations/blob/master/VSLive2016/Vegas/)
* [Wprowadzenie do platformy ASP.NET Core @ build 2016 — której możesz w wersji demonstracyjnej](https://channel9.msdn.com/Events/Build/2016/B810)
* [Tworzenie aplikacji .NET w kontenerach, Channel 9](https://blogs.msdn.microsoft.com/stevelasker/2016/02/19/developing-asp-net-apps-in-docker-containers/)
