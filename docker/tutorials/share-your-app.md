---
title: 'Samouczek platformy Docker — część 3: udostępnianie aplikacji'
description: Opisuje sposób udostępniania obrazów platformy Docker przy użyciu Docker Hub rejestru.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d64d10c7abefc14f31c39c3b8397e95cec67e9f4
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222789"
---
# <a name="share-your-app"></a>Udostępnianie aplikacji

Teraz, gdy sbudowaliśmy obraz, udostępnijmy go! Aby udostępnić obrazy platformy Docker, należy użyć rejestru platformy Docker. Rejestr domyślny jest Docker Hub i jest to miejsce, z którego pochodzą wszystkie użyte przez nas obrazy.

## <a name="create-a-repo"></a>Tworzenie repo

Aby wypchnąć obraz, najpierw musisz utworzyć repo na Docker Hub.

1. Przejdź do [Docker Hub](https://hub.docker.com/signup/msftedge?utm_source=msftedge) i w razie potrzeby zaloguj się.

1. Kliknij przycisk **Create Repository (Utwórz repozytorium).**

1. Jako nazwę repo użyj `getting-started` . Upewnij się, że dla ustawienia Widoczność jest widoczna . `Public`

1. Kliknij przycisk **Utwórz.**

Jeśli spojrzysz po prawej stronie, zobaczysz sekcję o nazwie **Polecenia platformy Docker**. Spowoduje to przykładowe polecenie, które należy uruchomić, aby wypchnąć do tego repo.

![Polecenie platformy Docker z przykładem wypychania](media/push-command.png)

## <a name="push-the-image"></a>Wypychanie obrazu

1. W wierszu polecenia spróbuj uruchomić polecenie wypychania, które jest Docker Hub. Pamiętaj, że polecenie będzie używać przestrzeni nazw, a nie "docker".

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Dlaczego zakończyło się niepowodzeniem? Polecenie wypychania szukało obrazu o nazwie docker/getting-started, ale nie znalazło go. Jeśli uruchamiasz `docker image ls` , nie zobaczysz też jednego z nich.

    Aby rozwiązać ten problem, musisz "oznaczyć" istniejący obraz, który sbudowaliśmy, aby nadać mu inną nazwę.

1. Zaloguj się do aplikacji Docker Hub za pomocą polecenia `docker login -u <username>` .

1. Użyj polecenia `docker tag` , aby nadać `getting-started` obrazowi nową nazwę. Pamiętaj, aby zamienić `<username>` się z identyfikatorem platformy Docker.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Teraz spróbuj ponownie wykonać polecenie wypychania. Jeśli kopiujesz wartość z Docker Hub, możesz upuścić część, ponieważ nie dodasz `tagname` tagu do nazwy obrazu. Jeśli nie określisz tagu, docker użyje tagu o nazwie `latest` .

    ```bash
    docker push <username>/getting-started
    ```

    Zamiast wiersza polecenia możesz również kliknąć prawym przyciskiem myszy  tag obrazu w sekcji Obrazy w widoku platformy Docker, wybrać polecenie Wypchnąć..., a następnie wybrać pozycję Połączenie **registry..., a** następnie wybrać **Docker Hub**. 

## <a name="run-the-image-on-a-new-instance"></a>Uruchamianie obrazu w nowym wystąpieniu

Teraz, gdy obraz został sbudowaną i wypchniętą do rejestru, spróbuj uruchomić aplikację w zupełnie nowym wystąpieniu, które nigdy nie widziało tego obrazu kontenera. W tym celu użyjemy funkcji Play with Docker.

1. Otwórz przeglądarkę, aby [odtworzyć za pomocą platformy Docker.](http://play-with-docker.com)

1. Zaloguj się przy użyciu Docker Hub konta.

1. Po zalogowaniu kliknij link "+ DODAJ NOWE WYSTĄPIENIE" na pasku po lewej stronie. (Jeśli jej nie widzisz, przekszlij przeglądarkę). Po kilku sekundach w przeglądarce zostanie otwarte okno terminalu.

    ![Odtwarzanie przy użyciu platformy Docker w celu dodania nowego wystąpienia](media/pwd-add-new-instance.png)

1. W terminalu uruchom świeżo wypchniętą aplikację.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Obraz powinien zostać ściągnięty i po pewnym czasie powinien zostać wyświetlony.

1. Gdy się pojawia, kliknij wskaźnik 3000. Powinna zostać wyświetlony aplikacja z wprowadzonymi zmianami. Brawo! Jeśli znaczek 3000 nie jest pokazywany, możesz kliknąć przycisk Otwórz **port** i wpisać 3000.

## <a name="recap"></a>Podsumowanie

W tej sekcji opisano sposób udostępniania obrazów przez wypychanie ich do rejestru. Następnie poszło do zupełnie nowego wystąpienia i udało Ci się uruchomić świeżo wypchnięty obraz. Jest to dość typowe w potokach ciasnych, w których potok utworzy obraz i wypchnie go do rejestru, a następnie środowisko produkcyjne może użyć najnowszej wersji obrazu.

Teraz, gdy już wiesz, jak to zrobić, przypomnij sobie, że na końcu ostatniej sekcji, po ponownym uruchomieniu aplikacji, utracisz wszystkie elementy listy zadań do stracenia. Oczywiście nie jest to doskonałe środowisko użytkownika, dlatego dowiesz się, jak można utrwalić dane po ponownym uruchomieniu.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Utrwalanie bazy danych](persist-your-data.md)
