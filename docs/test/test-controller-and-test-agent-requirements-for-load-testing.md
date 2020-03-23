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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588645"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Wymagania dotyczące sterownika testowego i agenta testowego do testowania obciążenia

Kilka typów testów, w tym jednostki, wydajność sieci web, obciążenia i testów ręcznych są zintegrowane z programem Visual Studio. Visual Studio umożliwia użytkownikom zarządzania cyklem życia aplikacji programu Visual Studio uruchamianie testów na komputerach zdalnych przy użyciu kontrolera testów i co najmniej jednego agenta. Zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Wymagania dotyczące sprzętu i oprogramowania

Zarówno kontroler testów, jak i komputery agenta testowego mają określone wymagania sprzętowe i programowe. Ponadto jeśli chcesz wdrożyć kontroler testów i komputery agenta testowego w wielu językach, należy zaplanować sposób obsługi tych języków.

### <a name="hardware-requirements"></a>Wymagania sprzętowe

W poniższej tabeli przedstawiono zalecane wymagania sprzętowe dotyczące wdrażania kontrolera testów i agentów testowych.

|**Konfiguracja**|**Składnik**|**Procesora**|**HD**|**Pamięci**|
|-|-------------------|-|------------|-|
|< 500 wirtualnych użytkowników|Agent testowy|2,6 GHz|10 GB|2 GB|
|< 1000 wirtualnych użytkowników|Agent testowy|Dwuprocesorowy 2,6 GHz|10 GB|2 GB|
|N x 1000 wirtualnych użytkowników|Agent testowy|Skalowanie w poziomie do agentów N z dwoma 2,6 G/|10 GB|2 GB|
|\<30 komputerów w środowisku testowym. Dotyczy to również agentów i serwerów w fazie testów.|Kontroler testowy|2,6 GHz|||
|N x 30 komputerów w środowisku testowym. Dotyczy to również agentów i serwerów w fazie testów.|Kontroler testowy|Procesory N 2,6 GHz|||

> [!NOTE]
> Liczba użytkowników wirtualnych będzie się znacznie różnić w zależności od testu. Główną przyczyną tej wariancji jest wariancja w *czasie myślenia*lub opóźnienia użytkownika. Aby uzyskać więcej informacji, zobacz Edytowanie czasów myślenia w [celu symulacji opóźnień interakcji z człowiekiem w witrynie](../test/edit-think-times-in-load-test-scenarios.md). W teście obciążenia testy sieci web są na ogół bardziej wydajne i generują więcej obciążenia niż testy jednostkowe. Liczby w powyższej tabeli są prawidłowe do uruchamiania testów sieci web z 3-5 sekund czasu myślenia w typowej aplikacji sieci web.

Przedstawione tutaj wytyczne są dostarczane jako ogólne wskazówki dotyczące planowania sprzętu. Wydajność testu będzie się znacznie różnić w zależności od ilości danych testowych i liczby agentów testowych. W przypadku agentów testowych dostępna szybkość procesora i pamięć ograniczą obciążenie testowe. Kontrolery testów potrzebują większych zasobów, w zależności od liczby agentów testowych i ilości danych zaangażowanych w testy.

Serwer z uruchomionym programem Visual Studio powinien mieć niezawodne połączenie sieciowe o minimalnej przepustowości 1 Mb/s i maksymalnym opóźnieniu 350 ms. Nie powinno być zapory między agentami testowymi a kontrolerem testów. Jeśli wydajność testu nie spełnia twoich oczekiwań, należy rozważyć uaktualnienie konfiguracji sprzętu.

### <a name="additional-hardware-considerations"></a>Dodatkowe zagadnienia sprzętowe

Agenci testowi generują dużą ilość danych na kontrolerach testów, w zależności od czasu trwania testu i rozmiaru testu. Ogólnie rzecz biorąc należy zaplanować dodatkowe 10 GB pamięci masowej na dysku twardym dla każdego 24 godzin danych testowych.

Oprócz zalecanego w tym miejscu sprzętu należy wziąć pod uwagę dodatkowy sprzęt dla serwerów krytycznych, takich jak nadmiarowe zasilacze i nadmiarowe wentylatory.

### <a name="language-requirements"></a>Wymagania językowe

Aby uniknąć nieporozumień i uprościć działanie, kontroler testów i agentów testowych powinny być skonfigurowane do używania tego samego języka, co system operacyjny komputera i team foundation server. Jeśli agent testowy i kontroler testów są zainstalowane na różnych komputerach, muszą być skonfigurowane do używania tego samego języka. Można jednak zainstalować inną wersję językową programu Visual Studio w systemie operacyjnym w języku angielskim, o ile ten język jest zgodny z językiem wdrożenia programu Team Foundation Server.

## <a name="monitor-agent-resources"></a>Monitorowanie zasobów agenta

Można monitorować maszyny agenta, aby określić ich potrzeby zasobów, obserwując *procesy QTAgent\*.exe,* które wykonują i skalują podczas testów. Najczęstszym wąskim gardłem w procesach *qtagent\*.exe* jest wykorzystanie procesora CPU. Jeśli wykorzystanie procesora CPU jest konsekwentnie w latach dziewięćdziesiątych, to jest wskazanie, że agent jest ładowany mocno. Następnym typowym wąskim gardłem jest użycie pamięci. W przypadku wymagających testów monitorowanie tych zasobów może pomóc w określeniu, czy należy zwiększyć zasoby maszyn, czy rozprowadzić testy w inny sposób.

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
