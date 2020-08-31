---
title: 'Samouczek platformy Docker — część 2: aktualizowanie aplikacji'
description: Opisuje sposób aktualizowania aplikacji platformy Docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 4a1cba71481608803522336ad5c0f6b6354bca32
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2020
ms.locfileid: "89178440"
---
# <a name="update-the-app"></a>Aktualizowanie aplikacji

Jako żądanie dotyczące małych funkcji użytkownik otrzymał prośbę o zmianę "pustego tekstu", jeśli nie masz żadnych elementów listy zadań do wykonania. Chcą przenieść je do następujących:

> Nie masz jeszcze elementów do wykonania. Dodaj jeden powyżej!

Całkiem proste, w prawo? Wprowadźmy zmianę.

## <a name="update-the-source-code"></a>Aktualizowanie kodu źródłowego

1. W `src/static/js/app.js` pliku, zaktualizuj wiersz 56, aby użyć nowego pustego tekstu.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Utwórz zaktualizowaną wersję obrazu przy użyciu tego samego polecenia, które zostało użyte wcześniej.

    ```bash
    docker build -t getting-started .
    ```

1. Rozpocznij nowy kontener przy użyciu zaktualizowanego kodu.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**Zapomniano** Prawdopodobnie napotkasz błąd podobny do tego (identyfikatory będą różne):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Co się stało? Nie można rozpocząć nowego kontenera, ponieważ stary kontener nadal działa. Przyczyną tego problemu jest to, że ten kontener używa portu 3000 hosta, a tylko jeden proces na komputerze (kontenery zawarte) może nasłuchiwać określonego portu. Aby rozwiązać ten problem, usuń stary kontener.

## <a name="replace-the-old-container"></a>Zastąp stary kontener

Aby usunąć kontener, najpierw należy go zatrzymać. Po jego zatrzymaniu można go usunąć. Istnieją dwa sposoby usunięcia starego kontenera. Możesz wybrać najbardziej wygodną ścieżkę.

### <a name="remove-a-container-using-the-cli"></a>Usuwanie kontenera przy użyciu interfejsu wiersza polecenia

1. Pobierz identyfikator kontenera za pomocą `docker ps` polecenia.

    ```bash
    docker ps
    ```

1. Użyj `docker stop` polecenia, aby zatrzymać kontener.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Po zatrzymaniu kontenera można go usunąć za pomocą `docker rm` polecenia.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Można zatrzymać i usunąć kontener w pojedynczym poleceniu, dodając do polecenia flagę "Force" `docker rm` . Na przykład: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-dashboard"></a>Usuwanie kontenera przy użyciu pulpitu nawigacyjnego platformy Docker

Jeśli otworzysz rozszerzenie VS Code, możesz usunąć kontener z dwoma kliknięciami. Znacznie łatwiej jest wyszukać identyfikator kontenera i usunąć go.

1. Po otwarciu rozszerzenia przejdź do kontenera i kliknij prawym przyciskiem myszy.

1. Kliknij opcję **Usuń** .

1. Potwierdź usunięcie i wszystko gotowe!

![Pulpit nawigacyjny platformy Docker — usuwanie kontenera](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Uruchom zaktualizowany kontener aplikacji

1. Teraz uruchom zaktualizowaną aplikację.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Odśwież przeglądarkę w dniu [http://localhost:3000](http://localhost:3000) i zobaczysz zaktualizowany tekst pomocy.

![Zaktualizowano aplikację z zaktualizowanym pustym tekstem](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Podsumowanie

Podczas tworzenia aktualizacji wystąpiły dwie rzeczy, które mogły być zauważalne:

- Wszystkie istniejące elementy na liście zadań do wykonania zostały utracone. To nie jest dobra aplikacja. Wkrótce skontaktujemy się z Tobą.
- Istniało *wiele* kroków, których dotyczy taka mała zmiana. W kolejnej sekcji znajdziesz informacje na temat sposobu wyświetlania aktualizacji kodu bez konieczności ponownego kompilowania i uruchamiania nowego kontenera przy każdym wprowadzeniu zmiany.

Przed rozpoczęciem uczenia się o trwałości można szybko zobaczyć, jak udostępnić te obrazy innym osobom.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Udostępnianie aplikacji](share-your-app.md)
