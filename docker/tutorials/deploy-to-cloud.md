---
title: 'Samouczek platformy Docker — część 9: wdrażanie w chmurze'
description: Wdróż aplikację platformy Docker w usłudze w chmurze na potrzeby hostingu.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 661f9f6833b5ac5d42aacde7f228b042bef00bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89178456"
---
# <a name="deploy-to-the-cloud"></a>Wdrażanie w chmurze

Teraz, gdy aplikacja jest uruchamiana lokalnie, możesz zacząć myśleć o uruchamianiu jej w chmurze, aby inne osoby mogły uzyskać do niej dostęp i korzystać z niej. W tym celu użyj kontekstów platformy Docker. Kontekst jest miejscem, w którym aktualnie pracujesz z kontenerami. Teraz masz tylko kontekst "default", więc musisz dodać chmurę i wdrożyć w niej aplikację.

## <a name="create-your-cloud-context"></a>Tworzenie kontekstu chmury

1. Aby rozpocząć, możesz zobaczyć, jakie konteksty masz, przeglądając sekcję kontekstowe w panelu Docker:

   ![Pokazuje tylko kontekst domyślny](media/defaultcontext.png)

Należy tylko zobaczyć domyślny kontekst dla pracy lokalnej.

1. Aby wdrożyć w chmurze, musisz utworzyć nowy kontekst ACI, ale w tym celu należy najpierw zainstalować rozszerzenie konta platformy Azure w celu uwierzytelnienia na platformie Azure.

   ![Dodawanie rozszerzenia platformy Azure](media/addazureextension.png)

Jeśli jeszcze tego nie zrobiono, należy skonfigurować konto platformy Azure.

1. Teraz możesz utworzyć nowy kontekst ACI. Możesz to zrobić, klikając przycisk Plus w sekcji **konteksty** w widoku platformy Docker.

   ![Tworzenie kontekstu ACI](media/createnewcontext.png)

Spowoduje to wyświetlenie pytania o grupę zasobów, w której mają być uruchamiane te kontenery. Wybierz istniejącą grupę przy użyciu klawiszy strzałek lub użyj opcji domyślnej, aby użyć nowej grupy.

![Wybieranie grupy zasobów](media/selectresourcegroup.png)

Zobaczysz teraz kontekst ACI i możesz go kliknąć prawym przyciskiem myszy, aby ustawić go jako bieżący kontekst/w użyciu:

![Można wybrać nowy kontekst ACI](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Uruchamianie kontenerów w chmurze

1. Teraz Użyj kontekstu ACI i uruchom kontener.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Po uruchomieniu tego elementu należy teraz przyjrzeć się kontenerowi w Twoim kontekście.

   ![Kontener uruchomiony w kontekście ACI](media/contextcontainer.png)

1. Aby sprawdzić, czy wszystko działa prawidłowo, kliknij prawym przyciskiem myszy uruchomiony kontener i wybierz polecenie **Wyświetl w przeglądarce**.

   ![Kontener w ACI z publicznym adresem IP](media/containerinaci.png)

Można też zobaczyć, że kontener jest uruchomiony w publicznym adresie IP i działa prawidłowo.

1. Teraz możesz przyjrzeć się naszemu uruchomionemu kontenerowi, aby zobaczyć, jak działa. Aby rozpocząć, należy zapoznać się z dziennikami kontenerów:
 
 ```bash
   docker logs distracted-jackson
   ```

1. Możesz również umieścić w kontenerze, tak jak w przypadku kontenera lokalnego.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Wreszcie, aby wyczyścić miejsce pracy i upewnić się, że nie są naliczane opłaty za kontynuowanie uruchamiania kontenera testowego, możesz po prostu kliknąć prawym przyciskiem myszy uruchomiony kontener i wybrać polecenie **Usuń**.

## <a name="recap"></a>Podsumowanie

Fantastycznie teraz wykonano obciążenie i wdrożono je w chmurze po raz pierwszy. Wszystkie te czynności można wykonać z poziomu wiersza polecenia, a także z poziomu kontekstu ACI przy użyciu `docker run` , a także `docker compose up` do uruchamiania aplikacji wielokontenerowych. Aby dowiedzieć się więcej o uruchamianiu kontenerów w chmurze, zapoznaj się z rozszerzoną [dokumentacją dotyczącą korzystania](https://docs.docker.com/engine/context/aci-integration/)z usługi ACI.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Co dalej](whats-next.md)
