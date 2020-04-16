---
title: Publikowanie aplikacji Node.js w usłudze App Service w systemie Linux
description: Aplikacje Node.js utworzone w programie Visual Studio w usłudze Linux App Service można publikować na platformie Azure
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d75bb4f5274201b7cf745ff8c7c6f27b869855c3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445015"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Publikowanie aplikacji Node.js na platformie Azure (linux App Service)

W tym samouczku można utworzyć prostą aplikację Node.js i opublikować ją na platformie Azure.

Podczas publikowania aplikacji Node.js na platformie Azure, istnieje kilka opcji. Należą do nich usługa Azure App Service, maszyna wirtualna z wybranym systemem operacyjnym, usługa Azure Container Service (AKS) do zarządzania za pomocą usługi Kubernetes, wystąpienie kontenera przy użyciu platformy Docker i inne. Aby uzyskać więcej informacji na temat każdej z tych opcji, zobacz [Oblicz .](https://azure.microsoft.com/product-categories/compute/)

W tym samouczku można wdrożyć aplikację do [usługi Linux App Service](/azure/app-service/containers/app-service-linux-intro).
Usługa aplikacji Linux App Service wdraża kontener platformy Docker systemu Linux w celu uruchomienia aplikacji Node.js (w przeciwieństwie do usługi Windows App Service, która uruchamia aplikacje Node.js za usługami IIS w systemie Windows).

W tym samouczku pokazano, jak utworzyć aplikację Node.js, zaczynając od szablonu zainstalowanego za pomocą narzędzia Node.js Tools for Visual Studio, wypchnąć kod do repozytorium w usłudze GitHub, a następnie aprowizować usługę Azure App Service za pośrednictwem portalu sieci Web platformy Azure, dzięki czemu można wdrożyć z repozytorium Usługi GitHub. Aby użyć wiersza polecenia do aprowizowania usługi Azure App Service i wypchnięcia kodu z lokalnego repozytorium Git, zobacz [Tworzenie aplikacji Node.js](/azure/app-service/containers/quickstart-nodejs).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu z użyciem narzędzia Node.js
> * Tworzenie repozytorium GitHub dla kodu
> * Tworzenie usługi aplikacji systemu Linux na platformie Azure
> * Wdrażanie w systemie Linux

## <a name="prerequisites"></a>Wymagania wstępne

* Musi być zainstalowany program Visual Studio i obciążenie deweloperskie node.js.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli chcesz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Wybierz obciążenie **deweloperne node.js,** a następnie wybierz pozycję **Modyfikuj**.

    ![Obciążenie node.js w instalatorze usługi VS](../ide/media/quickstart-nodejs-workload.png)

* Musi być zainstalowany środowisko uruchomieniowe Node.js.

    Jeśli nie masz go zainstalowanego, zainstaluj wersję LTS z [witryny node.js.](https://nodejs.org/en/download/) Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt tak, aby odwoływał się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Tworzenie projektu node.js do uruchomienia na platformie Azure

1. Otwórz program Visual Studio.

1. Utwórz nową aplikację TypeScript Express.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **Node.js**, a następnie wybierz pozycję **Utwórz nową podstawową aplikację Azure Node.js Express 4** (TypeScript). W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **TypeScript**, a następnie wybierz polecenie **Node.js**. W środkowym okienku wybierz pozycję **Basic Azure Node.js Express 4 application**, a następnie wybierz przycisk **OK**.

    ![Tworzenie nowej aplikacji TypeScript Express](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **aplikacji Basic Azure Node.js Express 4,** musisz dodać obciążenie **deweloperne node.js.** Aby uzyskać szczegółowe instrukcje, zobacz [Wymagania wstępne](#prerequisites).

    Program Visual Studio tworzy projekt i otwiera go w Eksploratorze rozwiązań (prawe okienko).

1. Naciśnij **klawisz F5,** aby utworzyć i uruchomić aplikację i upewnij się, że wszystko działa zgodnie z oczekiwaniami.

1. Wybierz **pozycję Dodaj plik** > **do formantu źródłowego,** aby utworzyć lokalne repozytorium Git dla projektu.

    W tym momencie aplikacja Node.js przy użyciu platformy Express i napisane w języku TypeScript działa i zaewidencjonowany do kontroli źródła lokalnego.

1. Edytuj projekt zgodnie z potrzebami przed przejściem do następnych kroków.

## <a name="push-code-from-visual-studio-to-github"></a>Wypychanie kodu z programu Visual Studio do usługi GitHub

Aby skonfigurować github dla programu Visual Studio:

1. Upewnij się, że [rozszerzenie GitHub dla programu Visual Studio](https://visualstudio.github.com/) jest zainstalowane i włączone przy użyciu elementu menu Rozszerzenia i**aktualizacje** **narzędzi** > .

2. Z menu wybierz **Pozycję Wyświetl** > **inne usługi Windows** > **GitHub**.

    Zostanie otwarte okno GitHub.

3. Jeśli nie widzisz przycisku **Wprowadzenie** w oknie GitHub, kliknij pozycję Dodaj **plik** > **do kontroli źródła** i poczekaj na aktualizację interfejsu użytkownika.

    ![Otwieranie okna Usługi GitHub](../javascript/media/azure-github-get-started.png)

4. Kliknij **pozycję Wprowadzenie**.

    Jeśli masz już połączenie z usługą GitHub, zestaw narzędzi jest podobny do poniższej ilustracji.

    ![Ustawienia repozytorium GitHub](../javascript/media/azure-github-publish.png)

5. Wypełnij pola dla nowego repozytorium do opublikowania, a następnie kliknij przycisk **Publikuj**.

    Po kilku chwilach pojawia się baner z napisem "Repozytorium utworzone pomyślnie".

    W następnej sekcji dowiesz się, jak opublikować z tego repozytorium do usługi Azure App Service w systemie Linux.

## <a name="create-a-linux-app-service-in-azure"></a>Tworzenie usługi aplikacji systemu Linux na platformie Azure

1. Zaloguj się w witrynie [Azure Portal](https://portal.azure.com).

2. Wybierz **pozycję Usługi aplikacji** z listy usług po lewej stronie, a następnie kliknij przycisk **Dodaj**.

3. W razie potrzeby utwórz nową grupę zasobów i plan usługi App Service do obsługi nowej aplikacji.

4. Upewnij się, aby ustawić **system operacyjny** na **Linux**i ustawić **Runtime Stack** do wymaganej wersji Node.js, jak pokazano na ilustracji.

    ![Tworzenie usługi aplikacji dla systemu Linux](../javascript/media/azure-create-appservice-annotated.png)

5. Kliknij **przycisk Utwórz,** aby utworzyć usługę app service.

    Wdrożenie może potrwać kilka minut.

6. Po wdrożeniu przejdź do sekcji **Ustawienia aplikacji** i dodaj `SCM_SCRIPT_GENERATOR_ARGS` ustawienie z `--node`nazwą i wartością .

    ![Ustawienia aplikacji](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Proces wdrażania usługi App Service używa zestawu heurystyki, aby określić, jaki typ aplikacji należy wypróbować i uruchomić. Jeśli . *Sln* plik jest wykrywany w wdrożonej zawartości, zakłada, że projekt oparty na MSBuild jest wdrażany. Powyższe ustawienie zastępuje tę logikę i wyraźnie określa, że jest to aplikacja Node.js. Bez tego ustawienia aplikacja Node.js nie zostanie wdrożona, jeśli plik . *sln* plik jest częścią repozytorium wdrażane w usłudze App Service.

7. W obszarze **Ustawienia aplikacji**dodaj kolejne `WEBSITE_NODE_DEFAULT_VERSION` ustawienie z `8.9.0`nazwą i wartością .

8. Po wdrożeniu otwórz usługę App Service i wybierz pozycję **Opcje wdrażania**.

    ![Opcje wdrożenia](../javascript/media/azure-deployment-options.png)

9. Kliknij **pozycję Wybierz źródło**, a następnie wybierz pozycję **GitHub**, a następnie skonfiguruj wymagane uprawnienia.

    ![Uprawnienia gitHub](../javascript/media/azure-choose-source.png)

10. Wybierz repozytorium i gałąź do opublikowania, a następnie wybierz **przycisk OK**.

    ![Publikowanie w usłudze App Service w systemie Linux](../javascript/media/azure-repo-and-branch.png)

    Strona **opcji wdrażania** jest wyświetlana podczas synchronizacji.

    ![Wdrażanie i synchronizowanie z usługą GitHub](../javascript/media/azure-deployment-options-sync.png)

    Po zakończeniu synchronizacji pojawi się znacznik wyboru.

    Witryna jest teraz uruchomiona aplikacja Node.js z repozytorium GitHub i jest dostępna pod adresem URL utworzonym dla usługi Azure App Service (domyślnie nazwa nadana usłudze Azure App Service, po której następuje ".azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Modyfikowanie aplikacji i wypychanie zmian

1. Dodaj kod pokazany tutaj w *app.ts* po wierszu `app.use('/users', users);`. Spowoduje to dodanie interfejsu API REST pod adresem URL */api*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Skompiluj kod i przetestuj go lokalnie, a następnie zaewidencjonuj go i wypchnij do gitHub.

    W witrynie Azure portal trwa kilka chwil, aby wykryć zmiany w repozytorium GitHub, a następnie rozpoczyna się nowa synchronizacja wdrożenia. Wygląda to podobnie do poniższej ilustracji.

    ![Modyfikowanie i synchronizowanie](../javascript/media/azure-changes-detected.png)

3. Po zakończeniu wdrażania przejdź do witryny publicznej i dołącz */api* do adresu URL. Odpowiedź JSON zostanie zwrócona.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

* Jeśli proces node.exe umiera (oznacza to, że występuje nieobsługiowany wyjątek), kontener zostanie ponownie uruchomiony.
* Po uruchomieniu kontenera, działa przez różne heurystyki, aby dowiedzieć się, jak rozpocząć proces Node.js. Szczegóły implementacji można zobaczyć na [generateStartupCommand.js](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js).
* Można połączyć się z uruchomionym kontenerem za pośrednictwem protokołu SSH w celu przeprowadzenia badań. Można to łatwo zrobić za pomocą witryny Azure portal. Wybierz usługę app service i przewiń listę narzędzi w dół, aż do osiągnięcia **SSH** w sekcji **Narzędzia programistyczne.**
* Aby ułatwić rozwiązywanie problemów, przejdź do ustawień **dzienników diagnostyki** usługi App Service i zmień ustawienie **rejestrowania kontenera platformy Docker** z **Wyłączone** na **System plików**. Dzienniki są tworzone w kontenerze pod */home/LogFiles/*_docker.log*i są dostępne w polu za pomocą protokołu SSH lub FTP(S).
* Do witryny można przypisać niestandardową nazwę domeny, a nie domyślnie przypisany adres URL *.azurewebsites.net. Aby uzyskać więcej informacji, zobacz temat [Mapuj domenę niestandardową](/azure/app-service/app-service-web-tutorial-custom-domain).
* Wdrożenie w lokacji tymczasowej do dalszych testów przed przejściem do środowiska produkcyjnego jest najlepszym rozwiązaniem. Aby uzyskać szczegółowe informacje na temat konfigurowania tego, zobacz temat [Tworzenie środowisk przejściowych](/azure/app-service/web-sites-staged-publishing).
* Więcej często zadawanych pytań można [znaleźć w usłudze aplikacji w systemie Linux.](/azure/app-service/containers/app-service-linux-faq)

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak utworzyć usługę aplikacji systemu Linux i wdrożyć aplikację Node.js w usłudze. Możesz dowiedzieć się więcej o Linux App Service.

> [!div class="nextstepaction"]
> [Usługa aplikacji dla systemu Linux](/azure/app-service/containers/app-service-linux-intro)
