---
title: Publikowanie aplikacji Node.js w usłudze App Service w systemie Linux
description: Można opublikować aplikacji Node.js w programie Visual Studio do usługi App Service Linux na platformie Azure
ms.date: 11/1/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f52e1cb8538204dbf0e29ccdadcc4cb2894255ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021874"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Publikowanie aplikacji Node.js na platformie Azure (Linux App Service)

Ten samouczek przeprowadzi Cię przez zadanie tworzenia prostej aplikacji Node.js i publikując je na platformie Azure.

Podczas publikowania aplikacji Node.js na platformie Azure, dostępnych jest kilka opcji. Należą do usługi Azure App Service, Maszynę wirtualną z systemem operacyjnym wybrane, Azure Container Service (AKS) do zarządzania przy użyciu rozwiązania Kubernetes, wystąpienia kontenera za pomocą platformy Docker i nie tylko. Aby uzyskać więcej informacji dotyczących każdej z tych opcji, zobacz [obliczenia](https://azure.microsoft.com/product-categories/compute/).

Na potrzeby tego samouczka, możesz wdrożyć aplikację w [usługi App Service Linux](/azure/app-service/containers/app-service-linux-intro).
Usługa App Service Linux wdraża kontenera platformy Docker w systemie Linux do uruchamiania aplikacji Node.js (w przeciwieństwie do usługi aplikacji Windows, która uruchamia aplikacje Node.js za usług IIS na Windows).

W tym samouczku pokazano, jak utworzyć aplikację Node.js, zaczynając od szablonu zainstalowane z narzędzia Node.js dla programu Visual Studio, wypychanie kodu do repozytorium w witrynie GitHub i następnie Udostępnij usługi Azure App Service za pośrednictwem portalu sieci web platformy Azure, dzięki czemu można wdrożyć z Repozytorium GitHub. Aby użyć wiersza polecenia do aprowizacji usługi Azure App Service i wypychanie kodu z lokalnego repozytorium Git, zobacz [tworzenie aplikacji Node.js](/azure/app-service/containers/quickstart-nodejs).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy Node.js
> * Utwórz repozytorium GitHub dla kodu
> * Tworzenie usługi App Service dla systemu Linux na platformie Azure
> * Wdrażanie w systemie Linux

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Tworzenie projektu środowiska Node.js do uruchamiania na platformie Azure

1. Utwórz nowy TypeScript Express aplikacji za pomocą **pliku** > **nowy projekt** okno dialogowe.

1. W obszarze **TypeScript** węzeł **podstawowe aplikację Node.js Express 4**.

    ![Utwórz nową aplikację TypeScript Express](../javascript/media/azure-ts-express-app.png)

1. Kliknij przycisk **OK** do utworzenia projektu w programie Visual Studio.

1. Naciśnij klawisz **F5** tworzenie i uruchamianie aplikacji i upewnij się, że wszystko działa zgodnie z oczekiwaniami.

1. Wybierz **pliku** > **Dodaj do kontroli źródła** do tworzenia lokalnego repozytorium Git dla projektu.

    W tym momencie Node.js aplikacji przy użyciu platformy Express i napisanych w TypeScript działa i zaewidencjonowane do kontroli źródła lokalnego.

1. Edytuj projekt zgodnie z potrzebami przed przejściem do następnych kroków.

## <a name="push-code-from-visual-studio-to-github"></a>Wypychanie kodu w programie Visual Studio do usługi GitHub

Aby skonfigurować usługi GitHub dla programu Visual Studio:

1. Upewnij się, że [rozszerzeniu GitHub Extension for Visual Studio](https://visualstudio.github.com/) jest zainstalowana i włączona przy użyciu elementu menu **narzędzia** > **rozszerzenia i aktualizacje**.

2. Wybierz z menu **widoku** > **Windows inne** > **GitHub**.

    Zostanie otwarte okno usługi GitHub.

3. Jeśli nie widzisz **wprowadzenie** znajdujący się w oknie usługi GitHub, kliknij przycisk **pliku** > **Dodaj do kontroli źródła** i poczekaj, aż interfejs użytkownika do zaktualizowania.

    ![Otwórz okno usługi GitHub](../javascript/media/azure-github-get-started.png)

4. Kliknij przycisk **wprowadzenie**.

    Jeśli jesteś podłączony do serwisu GitHub, Przybornik pojawi się podobnie jak na poniższej ilustracji.

    ![Ustawienia repozytorium GitHub](../javascript/media/azure-github-publish.png)

5. Wypełnij pola dla nowego repozytorium, aby opublikować, a następnie kliknij przycisk **Publikuj**.

    Po kilku chwilach zostanie wyświetlony transparent z informacją "Repozytorium utworzony pomyślnie".

    W następnej sekcji dowiesz się, jak publikować z tego repozytorium w usłudze Azure App Service w systemie Linux.

## <a name="create-a-linux-app-service-in-azure"></a>Tworzenie usługi App Service dla systemu Linux na platformie Azure

1. Zaloguj się do witryny [Azure Portal](https://portal.azure.com).

2. Wybierz **App Services** z listy usług po lewej stronie, a następnie kliknij przycisk **Dodaj**.

3. W razie potrzeby utwórz nowy plan grupy zasobów i usługi App Service do hostowania nowej aplikacji.

4. Upewnij się ustawić **OS** do **Linux**i ustaw **stosu środowiska uruchomieniowego** do wymaganej wersji środowiska Node.js, jak pokazano na ilustracji.

    ![Utwórz usługę App Service dla systemu Linux](../javascript/media/azure-create-appservice-annotated.png)

5. Kliknij przycisk **Utwórz** do tworzenia usługi App Service.

    Może upłynąć kilka minut, aby wdrożyć.

6. Po jej wdrożeniu, przejdź do **ustawienia aplikacji** sekcji i Dodaj ustawienie o nazwie `SCM_SCRIPT_GENERATOR_ARGS` oraz wartość `--node`.

    ![Ustawienia aplikacji](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Proces wdrażania usługi App Service używa zestawu algorytmów heurystycznych, aby określić, jakiego typu aplikacji i spróbuj uruchomić. Jeśli. *sln* wykrycia wdrożoną zawartością pliku, przyjmie jest wdrażany projekt na podstawie programu MSBuild. Ustawienie dodanych wcześniej zastępuje tę logikę i jawnie określa, że jest to aplikacja Node.js. Bez tego ustawienia aplikacji Node.js zakończy się niepowodzeniem do wdrożenia, jeśli. *sln* plik jest częścią repozytorium wdrażana w usłudze App Service.

7. Po jej wdrożeniu, otwórz usługi App Service i wybierz **opcje wdrażania**.

    ![Opcje wdrażania](../javascript/media/azure-deployment-options.png)

8. Kliknij przycisk **wybierz źródło**, a następnie wybierz **GitHub**, a następnie skonfiguruj wszystkie wymagane uprawnienia.

    ![Uprawnień w usłudze GitHub](../javascript/media/azure-choose-source.png)

9. Wybierz repozytorium i gałęzi do publikowania, a następnie wybierz **OK**.

    ![Publikowanie w usłudze App Service w systemie Linux](../javascript/media/azure-repo-and-branch.png)

    **Opcje wdrażania** podczas synchronizowania zostanie wyświetlona strona.

    ![Wdrażanie i synchronizowania za pomocą usługi GitHub](../javascript/media/azure-deployment-options-sync.png)

    Po zakończeniu synchronizacji, zostanie wyświetlony znacznik wyboru.

    Witryna jest teraz uruchomiona jest aplikacja Node.js z repozytorium GitHub, a nie jest dostępny pod adresem URL utworzonych dla usługi Azure App Service (domyślnie następuje nazwa nadana w usłudze Azure App Service ". azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Modyfikowanie aplikacji i wypychanie zmian

1. Dodaj kod przedstawiony tutaj w *app.ts* po wierszu `app.use('/users', users);`. Spowoduje to dodanie interfejsu API REST pod adresem URL */interfejs API*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Tworzenie kodu i testowanie go lokalnie, następnie zaewidencjonuj go i Wypychanie do usługi GitHub.

    W witrynie Azure portal może potrwać kilka minut wykrywanie zmian w repozytorium GitHub, a następnie uruchamia synchronizację nowego wdrożenia. To wygląda podobnie do poniższej ilustracji.

    ![Zmodyfikuj i synchronizacji](../javascript/media/azure-changes-detected.png)

3. Po zakończeniu wdrażania przejdź do witryny publicznej i Dołącz */interfejs API* do adresu URL. Pobiera zwrócił odpowiedź w formacie JSON.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

* Jeśli node.exe procesu śmierci (oznacza to, że wystąpi nieobsługiwany wyjątek), ponownego uruchamiania kontenera.
* Podczas uruchamiania kontenera jest uruchamiany za pośrednictwem różnych Algorytm heurystyczny, aby dowiedzieć się, jak można uruchomić procesu Node.js. Szczegóły wdrożenia są widoczne w [generateStartupCommand.js](https://github.com/Azure-App-Service/node/blob/master/8.9.4/startup/generateStartupCommand.js).
* Możesz połączyć się z działającym kontenerem za pośrednictwem protokołu SSH dla badania. Łatwo to zrobić przy użyciu witryny Azure Portal. Wybierz usługi App Service, a następnie przewiń w dół listy narzędzi aż do osiągnięcia **SSH** w obszarze **narzędzia programistyczne** sekcji.
* Aby ułatwić rozwiązywanie problemów, przejdź do **dzienniki diagnostyczne** ustawienia dla usługi App Service, a następnie zmień **rejestrowanie kontenerów Docker** ustawienie z **poza** do  **System plików**. Dzienniki są tworzone w kontenerze w ramach */home/LogFiles/*_docker.log* i jest dostępny w usłudze box przy użyciu klienta SSH lub FTP (S).
* Niestandardowej nazwy domeny może być przypisana do lokacji, a nie *. domyślnie przypisane adresu URL azurewebsites.net. Aby uzyskać więcej informacji, zobacz temat [domena niestandardowa mapy](/azure/app-service/app-service-web-tutorial-custom-domain).
* Wdrażanie przejściowej lokacji celach dalszego testowania przed przejściem do produkcji jest najlepszym rozwiązaniem. Aby uzyskać szczegółowe informacje na temat sposobu skonfigurowania tego ustawienia, zobacz temat [tworzenie środowisk przejściowych](/azure/app-service/web-sites-staged-publishing).
* Zobacz [usługi App Service w systemie Linux — często zadawane pytania](/azure/app-service/containers/app-service-linux-faq) dla często zadawane pytania.

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób tworzenia usługi App Service dla systemu Linux i wdrażanie aplikacji Node.js z usługą. Można dowiedzieć się więcej o usłudze App Service w systemie Linux.

> [!div class="nextstepaction"]
> [Usługa App Service w systemie Linux](/azure/app-service/containers/app-service-linux-intro)
