---
title: 'Samouczek platformy Docker — część 2: aktualizowanie aplikacji'
description: Opisuje sposób aktualizowania aplikacji platformy Docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 43034ff2e65564cc8af2710b796b76996f21f4c8
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222776"
---
# <a name="update-the-app"></a>Aktualizowanie aplikacji

W przypadku niewielkiego żądania funkcji zespół produktu poprosił Cię o zmianę "pustego tekstu" w przypadku, gdy nie masz żadnych elementów listy zadań do oddo. Chcą go przesłonić do następujących:

> Nie masz jeszcze żadnych rzeczy do zdjęć! Dodaj jeden z nich powyżej!

Proste, prawda? Dokonajmy zmiany.

## <a name="update-the-source-code"></a>Aktualizowanie kodu źródłowego

1. W pliku `src/static/js/app.js` zaktualizuj wiersz 56, aby użyć nowego pustego tekstu.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Skompilowanie zaktualizowanej wersji obrazu przy użyciu tego samego polecenia, które było używane wcześniej.

    ```bash
    docker build -t getting-started .
    ```

1. Uruchom nowy kontener przy użyciu zaktualizowanego kodu.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**Och!** Prawdopodobnie wystąpił błąd podobny do tego (identyfikatory będą inne):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Co się stało? Nie można uruchomić nowego kontenera, ponieważ stary kontener nadal działa. Przyczyną tego problemu jest to, że kontener używa portu 3000 hosta, a tylko jeden proces na maszynie (dołączone kontenery) może nasłuchiwać określonego portu. Aby rozwiązać ten problem, usuń stary kontener.

## <a name="replace-the-old-container"></a>Zastępowanie starego kontenera

Aby usunąć kontener, najpierw należy go zatrzymać. Po zatrzymaniu można go usunąć. Możesz usunąć stary kontener na dwa sposoby. Możesz wybrać ścieżkę, która jest dla Ciebie najbardziej wygodna.

### <a name="remove-a-container-using-the-cli"></a>Usuwanie kontenera przy użyciu interfejsu wiersza polecenia

1. Pobierz identyfikator kontenera za pomocą `docker ps` polecenia .

    ```bash
    docker ps
    ```

1. Użyj polecenia `docker stop` , aby zatrzymać kontener.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Po zatrzymaniu kontenera możesz go usunąć za pomocą `docker rm` polecenia .

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Kontener można zatrzymać i usunąć za pomocą jednego polecenia, dodając flagę "force" do `docker rm` polecenia . Na przykład: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-view"></a>Usuwanie kontenera przy użyciu widoku platformy Docker

Jeśli otworzysz rozszerzenie VS Code, możesz usunąć kontener za pomocą dwóch kliknięć. Na pewno znacznie łatwiej jest znaleźć identyfikator kontenera i go usunąć.

1. Po otwarciu rozszerzenia przejdź do kontenera i kliknij go prawym przyciskiem myszy.

1. Kliknij opcję **Usuń.**

1. Potwierdź usunięcie i gotowe!

![Widok platformy Docker — usuwanie kontenera](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Uruchamianie zaktualizowanego kontenera aplikacji

1. Teraz uruchom zaktualizowaną aplikację.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Odśwież przeglądarkę i [http://localhost:3000](http://localhost:3000) powinien zostać wyświetlony zaktualizowany tekst pomocy.

![Zaktualizowano aplikację przy użyciu zaktualizowanego pustego tekstu](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Podsumowanie

Podczas tworzenia aktualizacji można było zauważyć dwie rzeczy:

- Wszystkie elementy na liście zadań do zdjęć zostały już zniknęły. To nie jest bardzo dobra aplikacja. Wkrótce o tym porozmawiamy.
- Było wiele *kroków związanych* z tak małą zmianą. W nadchodzącej sekcji dowiesz się, jak wyświetlić aktualizacje kodu bez konieczności ponownego kompilowania i uruchamiania nowego kontenera za każdym razem, gdy zmieniasz.

Zanim poznasz trwałość, szybko zobaczysz, jak udostępniać te obrazy innym osobom.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Udostępnianie aplikacji](share-your-app.md)
