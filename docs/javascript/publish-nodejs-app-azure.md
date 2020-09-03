---
title: Publikowanie aplikacji Node.js w usłudze App Service w systemie Linux
description: Możesz publikować Node.js aplikacje utworzone w programie Visual Studio w systemie Linux App Service na platformie Azure
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81445015"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Publikowanie aplikacji Node.js na platformie Azure (App Service z systemem Linux)

Ten samouczek przeprowadzi Cię przez zadanie tworzenia prostej aplikacji Node.js i publikowania jej na platformie Azure.

W przypadku publikowania aplikacji Node.js na platformie Azure istnieje kilka opcji. Obejmują one Azure App Service, maszynę wirtualną, na której działa system operacyjny, Azure Container Service (AKS) do zarządzania za pomocą Kubernetes, wystąpienia kontenera przy użyciu platformy Docker i innych. Aby uzyskać więcej informacji na temat każdej z tych opcji, zobacz [COMPUTE](https://azure.microsoft.com/product-categories/compute/).

W tym samouczku aplikacja zostanie wdrożona w [App Service systemu Linux](/azure/app-service/containers/app-service-linux-intro).
System Linux App Service wdraża kontener platformy Docker systemu Linux w celu uruchomienia aplikacji Node.js (w przeciwieństwie do App Service Windows, w którym są uruchamiane Node.js aplikacje za pomocą usług IIS w systemie Windows).

W tym samouczku pokazano, jak utworzyć aplikację Node.js, rozpoczynając od szablonu zainstalowanego za pomocą narzędzi Node.js Tools for Visual Studio, wypchnięcia kodu do repozytorium w usłudze GitHub, a następnie udostępnienia Azure App Service za pośrednictwem portalu sieci Web systemu Azure, dzięki czemu można wdrożyć z repozytorium GitHub. Aby użyć wiersza polecenia do aprowizacji Azure App Service i wypchnięcia kodu z lokalnego repozytorium git, zobacz [Tworzenie aplikacji Node.js](/azure/app-service/containers/quickstart-nodejs).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy Node.js
> * Utwórz repozytorium GitHub dla kodu
> * Tworzenie App Service z systemem Linux na platformie Azure
> * Wdrażanie w systemie Linux

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i Node.js obciążenie programowaniem.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/),   Aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/),   Aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje..**., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz **Node.js obciążenie programowaniem** , a następnie wybierz **Modyfikuj**.

    ![Node.js obciążenie w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

* Musisz mieć zainstalowane środowisko uruchomieniowe Node.js.

    Jeśli go nie zainstalowano, Zainstaluj wersję LTS z witryny sieci Web [Node.js](https://nodejs.org/en/download/) . Ogólnie rzecz biorąc, program Visual Studio automatycznie wykrywa zainstalowane Node.js środowiska uruchomieniowego. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt do odwoływania się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Tworzenie projektu Node.js do uruchamiania na platformie Azure

1. Otwórz program Visual Studio.

1. Utwórz nową aplikację TypeScript Express.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **Node.js**, a następnie wybierz pozycję **utwórz nową podstawową aplikację Azure Node.js Express 4** (TypeScript). W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **TypeScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz pozycję **podstawowa aplikacja Azure Node.js Express 4**, a następnie wybierz przycisk **OK**.

    ![Tworzenie nowej aplikacji języka TypeScript Express](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **podstawowe aplikacje platformy Azure Node.js Express 4** , musisz dodaćNode.js obciążenie ** programowaniem** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Program Visual Studio utworzy projekt i otworzy go w Eksplorator rozwiązań (prawego okienka).

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację, i upewnij się, że wszystko działa zgodnie z oczekiwaniami.

1. Wybierz pozycję **plik**  >  **Dodaj do kontroli źródła** , aby utworzyć lokalne repozytorium git dla projektu.

    W tym momencie aplikacja Node.js przy użyciu języka Express i zapisywana w języku TypeScript działa i zaewidencjonowano w lokalnej kontroli źródła.

1. Przed przejściem do następnego kroku Edytuj projekt zgodnie z potrzebami.

## <a name="push-code-from-visual-studio-to-github"></a>Wypychanie kodu z programu Visual Studio do usługi GitHub

Aby skonfigurować witrynę GitHub dla programu Visual Studio:

1. Upewnij się, że [rozszerzenie GitHub dla programu Visual Studio](https://visualstudio.github.com/) jest zainstalowane i włączone przy użyciu **narzędzi**elementów menu  >  **rozszerzenia i aktualizacje**.

2. Z menu wybierz pozycję **Wyświetl**  >  **inne usługi Windows**  >  **GitHub**.

    Zostanie otwarte okno usługi GitHub.

3. Jeśli nie widzisz przycisku **wprowadzenie** w oknie GitHub, kliknij pozycję **plik**  >  **Dodaj do kontroli źródła** i poczekaj na zaktualizowanie interfejsu użytkownika.

    ![Otwieranie okna GitHub](../javascript/media/azure-github-get-started.png)

4. Kliknij pozycję **Rozpocznij**.

    Jeśli masz już połączenie z usługą GitHub, Przybornik wygląda podobnie do poniższej ilustracji.

    ![Ustawienia repozytorium GitHub](../javascript/media/azure-github-publish.png)

5. Wypełnij pola nowego repozytorium do opublikowania, a następnie kliknij przycisk **Publikuj**.

    Po kilku chwilach zostanie wyświetlony transparent informujący o pomyślnym utworzeniu repozytorium.

    W następnej sekcji dowiesz się, jak publikować z tego repozytorium do Azure App Service w systemie Linux.

## <a name="create-a-linux-app-service-in-azure"></a>Tworzenie App Service z systemem Linux na platformie Azure

1. Zaloguj się w witrynie [Azure Portal](https://portal.azure.com).

2. Wybierz **App Services** z listy usług po lewej stronie, a następnie kliknij przycisk **Dodaj**.

3. W razie potrzeby utwórz nową grupę zasobów i App Service plan, aby hostować nową aplikację.

4. Upewnij się, że **system operacyjny** jest ustawiony na **Linux**, i ustaw dla **stosu środowiska uruchomieniowego** wymaganą wersję Node.js, jak pokazano na ilustracji.

    ![Tworzenie App Service systemu Linux](../javascript/media/azure-create-appservice-annotated.png)

5. Kliknij przycisk **Utwórz** , aby utworzyć App Service.

    Wdrożenie może potrwać kilka minut.

6. Po jego wdrożeniu przejdź do sekcji **Ustawienia aplikacji** i Dodaj ustawienie o nazwie `SCM_SCRIPT_GENERATOR_ARGS` i wartości `--node` .

    ![Ustawienia aplikacji](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Proces wdrażania App Service używa zestawu algorytmów heurystycznych w celu określenia typu aplikacji do wypróbowania i uruchomienia. Jeśli. plik *sln* został wykryty w wdrożonej zawartości, zakłada się, że projekt oparty na programie MSBuild jest wdrażany. Ustawienie dodane powyżej zastępuje tę logikę i jawnie określa, że jest to aplikacja Node.js. Bez tego ustawienia aplikacja Node.js nie zostanie wdrożona, jeśli. plik *sln* jest częścią repozytorium, które jest wdrażane do App Service.

7. W obszarze **Ustawienia aplikacji**Dodaj inne ustawienie o nazwie `WEBSITE_NODE_DEFAULT_VERSION` i wartości `8.9.0` .

8. Po wdrożeniu programu Otwórz App Service a następnie wybierz **Opcje wdrażania**.

    ![Opcje wdrożenia](../javascript/media/azure-deployment-options.png)

9. Kliknij pozycję **Wybierz źródło**, a następnie wybierz pozycję **GitHub**, a następnie skonfiguruj wymagane uprawnienia.

    ![Uprawnienia usługi GitHub](../javascript/media/azure-choose-source.png)

10. Wybierz repozytorium i gałąź do opublikowania, a następnie wybierz przycisk **OK**.

    ![Publikowanie w usłudze App Service w systemie Linux](../javascript/media/azure-repo-and-branch.png)

    Podczas synchronizacji zostanie wyświetlona strona **Opcje wdrażania** .

    ![Wdrażanie i synchronizowanie za pomocą usługi GitHub](../javascript/media/azure-deployment-options-sync.png)

    Po zakończeniu synchronizacji zostanie wyświetlony znacznik wyboru.

    Lokacja jest teraz uruchomiona Node.js aplikacji z repozytorium GitHub i jest dostępna przy użyciu adresu URL utworzonego dla Azure App Service (Domyślnie nazwa nadana Azure App Service, a następnie ". azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Modyfikowanie aplikacji i wypychanie zmian

1. Dodaj kod przedstawiony tutaj w *aplikacji App. TS* po wierszu `app.use('/users', users);` . Spowoduje to dodanie interfejsu API REST pod adresem URL */API*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Skompiluj kod i przetestuj go lokalnie, a następnie Zaewidencjonuj go i wypchnij do serwisu GitHub.

    W Azure Portal potrwa kilka chwil, aby wykryć zmiany w repozytorium GitHub, a następnie rozpocząć nową synchronizację wdrożenia. Wygląda to podobnie do poniższej ilustracji.

    ![Modyfikowanie i synchronizowanie](../javascript/media/azure-changes-detected.png)

3. Po zakończeniu wdrażania przejdź do witryny publicznej i Dołącz */API* do adresu URL. Odpowiedź JSON zostanie zwrócona.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

* Jeśli proces node.exe wystąpił (czyli Wystąpił nieobsługiwany wyjątek), kontener zostanie ponownie uruchomiony.
* Po uruchomieniu kontenera jest on uruchamiany przez różne algorytmy heurystyczne, aby ustalić, jak uruchomić proces Node.js. Szczegóły implementacji mogą być widoczne w [generateStartupCommand.js](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js).
* Można nawiązać połączenie z działającym kontenerem za pośrednictwem protokołu SSH w celu dochodzeń. Jest to łatwo wykonywane przy użyciu Azure Portal. Wybierz App Service i przewiń w dół listę narzędzi do momentu osiągnięcia protokołu **SSH** w sekcji **Narzędzia programistyczne** .
* Aby pomóc w rozwiązywaniu problemów, przejdź do ustawień **dzienników diagnostyki** dla App Service i zmień ustawienie **rejestrowania kontenera Docker** z **wyłączone** na **system plików**. Dzienniki są tworzone w kontenerze w obszarze */home/LogFiles/*_docker. log * i można uzyskać do niego dostęp przy użyciu protokołu SSH lub FTP (S).
* Do witryny można przypisać niestandardową nazwę domeny, a nie adres URL *. azurewebsites.net przypisany domyślnie. Aby uzyskać więcej informacji, zobacz temat [Mapowanie domeny niestandardowej](/azure/app-service/app-service-web-tutorial-custom-domain)w temacie.
* Najlepszym rozwiązaniem jest wdrożenie w lokacji tymczasowej w celu przeprowadzenia dalszych testów przed przejściem do środowiska produkcyjnego. Aby uzyskać szczegółowe informacje na temat sposobu konfigurowania tego elementu, zobacz temat [Tworzenie środowisk przejściowych](/azure/app-service/web-sites-staged-publishing)w temacie.
* Zapoznaj się z tematem [App Service w systemie Linux — często](/azure/app-service/containers/app-service-linux-faq) zadawane pytania.

## <a name="next-steps"></a>Następne kroki

W ramach tego samouczka nauczysz się, jak utworzyć App Service systemu Linux i wdrożyć aplikację Node.js w usłudze. Warto dowiedzieć się więcej o App Service systemu Linux.

> [!div class="nextstepaction"]
> [App Service systemu Linux](/azure/app-service/containers/app-service-linux-intro)
