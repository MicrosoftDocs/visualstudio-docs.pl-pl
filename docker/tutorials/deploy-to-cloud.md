---
title: 'Samouczek platformy Docker — część 9: wdrażanie w chmurze'
description: Wdrażanie aplikacji platformy Docker w usłudze w chmurze w celu hostowania.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: da38b7482396b0bf46f5566c0c4a5416c94e83eb
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222828"
---
# <a name="deploy-to-the-cloud"></a>Wdrażanie w chmurze

Teraz, po uruchomieniu aplikacji lokalnie, możesz zacząć myśleć o jej uruchomieniu w chmurze, aby inne osoby były w stanie uzyskać do niego dostęp i z niego korzystać. W tym celu użyjesz kontekstów platformy Docker. Kontekst to miejsce, w którym obecnie pracujesz z kontenerami. W tej chwili masz tylko domyślny kontekst, więc musisz dodać chmurę i wdrożyć w nim swoją aplikację.

## <a name="create-your-cloud-context"></a>Tworzenie kontekstu chmury

1. Aby rozpocząć, możesz zobaczyć, jakie konteksty masz, spoglądaj na sekcję kontekstów panelu platformy Docker:

   ![Pokazuje tylko domyślny kontekst](media/defaultcontext.png)

Powinien zostać wyświetlony tylko domyślny kontekst pracy lokalnej.

1. Aby wdrożyć w chmurze, należy utworzyć nowy kontekst usługi ACI, ale w tym celu należy najpierw uwierzytelnić się na platformie Azure za pomocą rozszerzenia konta platformy Azure.

   ![Dodawanie rozszerzenia platformy Azure](media/addazureextension.png)

Jeśli jeszcze go nie masz, musisz skonfigurować konto platformy Azure.

1. Teraz możesz utworzyć nowy kontekst ACI. Możesz to zrobić, klikając przycisk plusa w **sekcji Konteksty** widoku platformy Docker.

   ![Tworzenie kontekstu ACI](media/createnewcontext.png)

Zostanie pytanie o grupę zasobów, w której chcesz uruchomić te kontenery. Wybierz istniejącą grupę przy użyciu klawiszy strzałek lub użyj opcji domyślnej, aby użyć nowej grupy.

![Wybieranie grupy zasobów](media/selectresourcegroup.png)

Teraz możesz wyświetlić kontekst ACI na liście i kliknąć go prawym przyciskiem myszy, aby ustawić go jako bieżący fokus/w kontekście użycia:

![Można wybrać nowy kontekst ACI](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Uruchamianie kontenerów w chmurze

1. Teraz użyj kontekstu ACI i uruchom kontener.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Po uruchomieniu tej aplikacji przyjrzyj się kontenerowi w swoim kontekście.

   ![Kontener uruchomiony w kontekście ACI](media/contextcontainer.png)

1. Aby sprawdzić, czy wszystko działa prawidłowo, możesz kliknąć prawym przyciskiem myszy uruchomiony kontener i wybrać polecenie **Wyświetl w przeglądarce.**

   ![Kontener w UCI z publicznym adresem IP](media/containerinaci.png)

Widać też, że kontener działa w publicznym adresie IP i działa prawidłowo.

1. Teraz możesz przyjrzeć się uruchomionemu kontenerowi, aby zobaczyć, jak działa. Możesz zacząć od przyjrzenia się dziennikom kontenerów:
 
 ```bash
   docker logs distracted-jackson
   ```

1. W kontenerze można również wyedytować plik exec, tak jak w przypadku kontenera lokalnego.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Na koniec, aby wyczyścić obszar roboczy i upewnić się, że nie są naliczane opłaty za kontynuowanie uruchamiania kontenera testowego, możesz po prostu kliknąć prawym przyciskiem myszy uruchomiony kontener i wybrać polecenie **Usuń**.

## <a name="recap"></a>Podsumowanie

Po raz pierwszy udało Ci się pomyślnie wdrożyć obciążenie w chmurze. Wszystko to można zrobić z poziomu wiersza polecenia, a także z poziomu kontekstu usługi ACI przy użyciu polecenia , a także przy użyciu polecenia do uruchamiania `docker run` `docker compose up` aplikacji z wieloma kontenerami. Aby dowiedzieć się więcej na temat uruchamiania kontenerów w chmurze, zapoznaj się z rozszerzoną dokumentacją [dotyczącą korzystania z usługi ACI.](https://docs.docker.com/engine/context/aci-integration/)

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Co dalej](whats-next.md)
