---
title: 'Samouczek platformy Docker — część 3: udostępnianie aplikacji'
description: Opisuje sposób udostępniania obrazów platformy Docker przy użyciu rejestru usługi Docker Hub.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: ad9f7d329bf00e3fadd665cefea22a2301fdf695
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061787"
---
# <a name="share-your-app"></a>Udostępnianie aplikacji

Teraz, po zbudowaniu obrazu, udostępnij go! Aby udostępnić obrazy platformy Docker, należy użyć rejestru platformy Docker. Domyślnym rejestrem jest Aparat Docker Hub i jest to miejsce, w którym pochodzą wszystkie z użytych obrazów.

## <a name="create-a-repo"></a>Tworzenie repozytorium

Aby wypchnąć obraz, najpierw należy utworzyć repozytorium w usłudze Docker Hub.

1. Przejdź do [centrum platformy Docker](https://hub.docker.com/signup/msftedge?utm_source=msftedge) i zaloguj się, jeśli jest to konieczne.

1. Kliknij przycisk **Utwórz repozytorium** .

1. W polu Nazwa repozytorium Użyj `getting-started` . Upewnij się, że widoczność jest `Public` .

1. Kliknij przycisk **Utwórz** .

Jeśli zobaczysz po prawej stronie strony, zobaczysz sekcję o nazwie **Docker Commands**. Zapewnia to przykładowe polecenie, które należy uruchomić, aby przeprowadzić wypychanie do tego repozytorium.

![Polecenie Docker z przykładem push](media/push-command.png)

## <a name="push-the-image"></a>Wypychanie obrazu

1. W wierszu polecenia spróbuj uruchomić polecenie push w usłudze Docker Hub. Należy pamiętać, że polecenie będzie używać przestrzeni nazw, a nie "Docker".

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Dlaczego Wystąpił błąd? Polecenie push szuka obrazu o nazwie Docker/Find-Started, ale go nie znaleziono. Jeśli uruchomisz `docker image ls` program, nie zobaczysz jednego z nich.

    Aby rozwiązać ten problem, musisz mieć "tag" istniejący utworzony wcześniej obraz, aby nadać mu inną nazwę.

1. Zaloguj się do usługi Docker Hub przy użyciu polecenia `docker login -u <username>` .

1. Użyj `docker tag` polecenia, aby nadać `getting-started` obrazowi nową nazwę. Pamiętaj, aby zamienić go na `<username>` identyfikator platformy Docker.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Teraz spróbuj ponownie wykonać polecenie push. Jeśli kopiujesz wartość z usługi Docker Hub, możesz usunąć `tagname` część, ponieważ nie dodano znacznika do nazwy obrazu. Jeśli nie określisz znacznika, Docker użyje tagu o nazwie `latest` .

    ```bash
    docker push <username>/getting-started
    ```

    Zamiast wiersza polecenia, można również kliknąć prawym przyciskiem myszy tag obrazu w sekcji **obrazy** w widoku platformy Docker, a następnie wybrać polecenie **wypchnięcie...**, a następnie wybrać polecenie **Połącz rejestr...** , a następnie pozycję **Docker Hub**.

## <a name="run-the-image-on-a-new-instance"></a>Uruchamianie obrazu na nowym wystąpieniu

Teraz, gdy obraz został skompilowany i wypychany do rejestru, spróbuj uruchomić aplikację na zupełnie nowym wystąpieniu, które nigdy nie widziało tego obrazu kontenera! W tym celu użyjesz programu Play z platformą Docker.

1. Otwórz przeglądarkę, aby [zagrać z platformą Docker](http://play-with-docker.com).

1. Zaloguj się przy użyciu konta centrum platformy Docker.

1. Po zalogowaniu kliknij link "+ Dodaj nowe wystąpienie" na pasku po lewej stronie. (Jeśli nie widzisz go, Zwiększ szerokość przeglądarki). Po kilku sekundach okno terminalu zostanie otwarte w przeglądarce.

    ![Odtwórz przy użyciu Dodaj nowe wystąpienie platformy Docker](media/pwd-add-new-instance.png)

1. Na terminalu Rozpocznij swoją świeżą aplikację.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Obraz powinien zostać wyświetlony i ostatecznie uruchomiony.

1. Kliknij wskaźnik 3000, gdy pojawi się, a zobaczysz aplikację ze zmianami. Hura! Jeśli wskaźnik 3000 nie jest widoczny, możesz kliknąć przycisk **Otwórz port** i wpisać w 3000.

## <a name="recap"></a>Podsumowanie

W tej sekcji przedstawiono sposób udostępniania obrazów przez wypychanie ich do rejestru. Następnie poszło do nowego wystąpienia i udało Ci się uruchomić świeżo wypchnięcie obrazu. Jest to bardzo popularne w potokach CI, gdzie potok utworzy obraz i wypchnij go do rejestru, a następnie środowisko produkcyjne może użyć najnowszej wersji obrazu.

Teraz, po wykonaniu tych zadań, należy odwołać się na końcu ostatniej sekcji po ponownym uruchomieniu aplikacji. wszystkie elementy listy zadań do zrobienia zostały utracone. Oczywiście to nie jest doskonałe środowisko użytkownika, więc dowiesz się, jak można utrwalać dane przez ponowne uruchomienie.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Utrwalanie bazy danych](persist-your-data.md)
