---
title: Debugowanie aplikacji w lokalnym kontenerze platformy Docker | Dokumentacja firmy Microsoft
description: Dowiedz się, jak zmodyfikować aplikację, która jest uruchomiona w lokalnym kontenerze Docker, odśwież kontener za pomocą edytowania i odświeżania i ustawiania punktów przerwania do debugowania
services: container-service
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 03/01/2019
ms.author: ghogen
ms.openlocfilehash: 7f80681d4aa307675f73eac24d0fbe17c7c7b9a9
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323768"
---
# <a name="debugging-apps-in-a-local-docker-container"></a>Debugowanie aplikacji w lokalnym kontenerze platformy Docker

## <a name="overview"></a>Omówienie

Program Visual Studio 2017 zapewnia spójny sposób programowania w kontenerze platformy Docker i zweryfikowania aplikacji w środowisku lokalnym.
Nie trzeba ponownie uruchomić kontener każdorazowo, gdy wprowadzeniu zmiana w kodzie.
W tym artykule pokazano, jak funkcja "Edytuj i Odśwież" Aby uruchomić aplikację sieci Web platformy ASP.NET Core w lokalnym kontenerze Docker, wprowadź niezbędne zmiany, a następnie odśwież przeglądarkę, aby zobaczyć zmiany.
W tym artykule przedstawiono również sposób ustawiania punktów przerwania do debugowania.

## <a name="prerequisites"></a>Wymagania wstępne

Muszą być zainstalowane następujące narzędzia.

::: moniker range="vs-2017"

* [Program Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem programowania dla sieci Web.

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) z zainstalowanym obciążeniem programowania dla sieci Web.

::: moniker-end

Do uruchamiania kontenerów platformy Docker lokalnie, należy klient lokalnej platformy docker.
Możesz użyć [przybornika Docker](https://www.docker.com/products/docker-toolbox), które wymagają funkcji Hyper-V można wyłączyć lub można użyć [Docker for Windows](https://www.docker.com/get-docker), które korzysta z funkcji Hyper-V i wymaga systemu Windows 10.

Jeśli używasz przybornika platformy Docker, konieczne będzie [Konfigurowanie klienta platformy Docker](vs-azure-tools-docker-setup.md)

## <a name="1-create-a-web-app"></a>1. Tworzenie aplikacji sieci web

[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]

## <a name="2-edit-your-code-and-refresh"></a>2. Edytuj kod i odświeżanie

Możesz szybko iterować zmiany, możesz uruchomić aplikację w kontenerze i kontynuować wprowadzanie zmian, ich wyświetlania, jak w przypadku usługi IIS Express.

1. Ustaw konfigurację rozwiązania `Debug` i naciśnij klawisz  **&lt;klawiszy CTRL + F5 >** Aby skompilować obraz platformy docker i uruchomić go lokalnie.

    Gdy obraz kontenera został skompilowany i jest uruchomiona w kontenerze platformy Docker, Visual Studio uruchamia aplikację sieci Web w domyślnej przeglądarce.
    Jeśli używasz przeglądarki Microsoft Edge lub w przeciwnym razie błędami, zobacz [Rozwiązywanie problemów](vs-azure-tools-docker-troubleshooting-docker-errors.md) sekcji.
2. Przejdź do strony informacje, czyli, gdzie zamierzamy nasze zmiany.
3. Wróć do programu Visual Studio i Otwórz `Views\Home\About.cshtml`.
4. Dodaj następującą zawartość HTML do końca pliku, a następnie zapisz zmiany.

    ```html
    <h1>Hello from a Docker Container!</h1>
    ```

5. Wyświetlanie w oknie danych wyjściowych po ukończeniu kompilacji platformy .NET i wyświetlić te wiersze, wróć do przeglądarki, a następnie odśwież stronę informacje.

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down
   ```

6. Zmiany zostały zastosowane!

## <a name="3-debug-with-breakpoints"></a>3. Debugować z punktami przerwania

Często zmian będzie potrzebna jest dalsza inspekcji, korzystając z funkcji debugowania programu Visual Studio.

1. Wróć do programu Visual Studio i Otwórz `About.cshtml.cs`
2. Zastąp zawartość `OnGet` metoda następującym kodem:

   ```cs
       Message = "Your application description page from within a Container";
   ```

3. Ustaw punkt przerwania na lewo od linii kodu.
4. Naciśnij klawisz F5, aby rozpocząć debugowanie.
5. Przejdź do strony informacje, aby trafić punkt przerwania.
6. Przełącz się do programu Visual Studio, aby wyświetlić punkt przerwania i sprawdzić wartość komunikatu.

   ![Punkt przerwania](media/vs-azure-tools-docker-edit-and-refresh/breakpoint.png)

## <a name="summary"></a>Podsumowanie

Dzięki obsłudze platformy Docker w programie Visual Studio 2017 możesz uzyskać wydajność pracy lokalnie, za pomocą realizmu produkcji rozwijających się w kontenerze platformy Docker.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

[Rozwiązywanie problemów z programowanie Docker programu Visual Studio](vs-azure-tools-docker-troubleshooting-docker-errors.md)

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Więcej informacji na temat platformy Docker przy użyciu programu Visual Studio, Windows i platformy Azure

* [Tworzenie kontenerów za pomocą programu Visual Studio](/visualstudio/containers) — strona Centrum rozwoju kontenera
* [Integracja z platformą docker dla usługi Azure potoków](https://aka.ms/dockertoolsforvsts) — umożliwia tworzenie i wdrażanie kontenerów aparatu docker
* [Narzędzia aparatu docker dla programu Visual Studio Code](https://aka.ms/dockertoolsforvscode) — usługi w języka do edycji plików docker przy użyciu scenariuszy e2e mieszczących się
* [Informacje o kontenerze Windows](https://aka.ms/containers)— informacje o systemie Windows Server i serwera Nano Server
* [Usługa Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) - [dokumentacja usługi Azure Kubernetes Service](/azure/aks)
