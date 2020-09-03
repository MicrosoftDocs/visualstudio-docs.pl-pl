---
title: Wymagania dla kontrolera testów i agentów testowych niezbędnych do testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39b174b0b134fdfdf26570565aa6aa756ba43c92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75588645"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Wymagania dotyczące kontrolera testów i agentów testowych do testowania obciążenia

Kilka typów testów, takich jak jednostki, wydajność sieci Web, obciążenie i testy ręczne, są zintegrowane z Visual Studio. Program Visual Studio umożliwia użytkownikom zarządzania cyklem życia aplikacji programu Visual Studio uruchamianie testów na komputerach zdalnych przy użyciu kontrolera testów i jednego lub większej liczby agentów. Zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Wymagania dotyczące sprzętu i oprogramowania

Zarówno komputery kontrolera testów, jak i agenta testowego mają określone wymagania dotyczące sprzętu i oprogramowania. Ponadto, jeśli chcesz wdrożyć kontroler testów i komputery agentów testowych w wielu językach, musisz zaplanować obsługę tych języków.

### <a name="hardware-requirements"></a>Wymagania sprzętowe

W poniższej tabeli przedstawiono zalecane wymagania sprzętowe dotyczące wdrażania kontrolera testów i agentów testowych.

|**Konfiguracja**|**Składnik**|**Procesor CPU**|**HD**|**Pamięć**|
|-|-------------------|-|------------|-|
|Użytkownicy wirtualne < 500|Agent testowy|2,6 GHz|10 GB|2 GB|
|Użytkownicy wirtualne < 1000|Agent testowy|Dwuprocesorowy 2,6 GHz|10 GB|2 GB|
|N x 1000 wirtualnych użytkowników|Agent testowy|Skaluj w poziomie do N agentów przy użyciu dwóch 2,6 GHz|10GB|PRZEKRACZA|
|\< 30 komputerów w środowisku testowym. Obejmuje to agentów i serwery objęte testem.|Test Controller|2,6 GHz|||
|N x 30 komputerów w środowisku testowym. Obejmuje to agentów i serwery objęte testem.|Test Controller|Procesor N 2,6 GHz|||

> [!NOTE]
> Liczba użytkowników wirtualnych różni się znacznie od testu testowego. Kluczową przyczyną tego wariancji jest Wariancja w *czasie reakcji*lub opóźnienia użytkownika. Aby uzyskać więcej informacji, zobacz [Edytowanie czasów reakcji w celu symulowania opóźnień interakcji z witryną sieci Web](../test/edit-think-times-in-load-test-scenarios.md). W teście obciążenia testy sieci Web są zwykle wydajniejsze i generują więcej obciążenia niż testy jednostkowe. Liczby w powyższej tabeli są prawidłowe dla uruchamiania testów sieci Web z 3-5 sekund czasu reakcji w typowej aplikacji sieci Web.

Przedstawione tutaj wytyczne są dostępne jako ogólne wskazówki dotyczące planowania sprzętu. Wydajność testów będzie się znacznie różnić w zależności od ilości danych testowych i liczby agentów testowych. W przypadku agentów testowych szybkość procesora i dostępna pamięć spowodują ograniczenie obciążenia testowego. Kontrolery testów potrzebują większych zasobów, w zależności od liczby agentów testowych i ilości danych używanych w testach.

Serwer z uruchomionym programem Visual Studio powinien mieć niezawodne połączenie sieciowe z przepustowością minimalną 1 MB/s i opóźnieniem maksymalnie 350ms. Między agentami testowymi i kontrolerem testów nie powinna być Zapora. Jeśli wydajność testowa nie spełnia oczekiwań, należy rozważyć uaktualnienie konfiguracji sprzętowej.

### <a name="additional-hardware-considerations"></a>Dodatkowe zagadnienia dotyczące sprzętu

Agenci testowi generują duże ilości danych na kontrolerach testów, w zależności od czasu trwania testu i rozmiaru testu. Ogólnie rzecz biorąc, należy zaplanować dodatkowe 10 GB miejsca na dysku twardym dla każdego 24-godzinnego danych testowych.

Oprócz zalecanego sprzętu należy wziąć pod uwagę dodatkowy sprzęt dla serwerów krytycznych, takich jak nadmiarowe zasilacze i nadmiarowe wentylatory.

### <a name="language-requirements"></a>Wymagania językowe

Aby uniknąć nieporozumień i uproszczenia działania, kontroler testów i agenci testowi należy skonfigurować tak, aby używać tego samego języka co system operacyjny komputera i Team Foundation Server. Jeśli agent testowy i kontroler testów są zainstalowane na różnych komputerach, muszą być skonfigurowane do korzystania z tego samego języka. Można jednak zainstalować inną wersję językową programu Visual Studio w systemie operacyjnym w języku angielskim, o ile ten język jest zgodny z wdrożeniem Team Foundation Server.

## <a name="monitor-agent-resources"></a>Monitorowanie zasobów agentów

Można monitorować maszyny agentów w celu określenia ich potrzeb dotyczących zasobów, obserwując procesy *QTAgent \* . exe* , które są wykonywane i skalowane podczas testów. Najbardziej typowym wąskim gardłem w procesach *QTAgent \* . exe* jest użycie procesora CPU. Jeśli użycie procesora CPU w dużym stopniu nineties, oznacza to, że Agent jest ładowany silnie. Następnym typowym wąskim gardłem jest użycie pamięci. W przypadku wymagających testów monitorowanie tych zasobów może pomóc w ustaleniu, czy należy zwiększyć zasoby maszyn lub rozpowszechnić testy w inny sposób.

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
