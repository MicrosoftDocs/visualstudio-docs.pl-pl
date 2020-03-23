---
title: Konfigurowanie ASP.NET profilera do testów obciążenia
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0132401df33bd65d7e328307167b6c228155bb42
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169394"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Jak: Konfigurowanie ASP.NET profiler do testów obciążenia przy użyciu ustawień testu w programie Visual Studio

Karty danych diagnostycznych ASP.NET profilera można używać do zbierania informacji ASP.NET profilera. Ta karta danych diagnostycznych zbiera dane dotyczące wydajności dla ASP.NET aplikacji.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Tej karty danych diagnostycznych nie można używać w testach uruchamianych przy użyciu Menedżera testów firmy Microsoft. Karty diagnostycznej ASP.NET profilera z testami obciążenia przy użyciu tylko w sieci Web, która wymaga programu Visual Studio Enterprise.

Karta danych diagnostycznych ASP.NET profiler umożliwia zbieranie danych ASP.NET profilera z warstwy aplikacji po uruchomieniu testu obciążenia. Profilera nie należy uruchamiać dla długich testów obciążeniowych, na przykład trwających ponad godzinę. Wynika to z faktu, że plik profilera może się rozrosnąć, nawet do kilkuset megabajtów. Zamiast tego należy uruchomić krótsze testy obciążenia przy użyciu ASP.NET profilera, który nadal daje korzyści z głębokiej diagnozy problemów z wydajnością.

> [!NOTE]
> Karta danych diagnostycznych ASP.NET profile danych profilowania proces internetowych usług informacyjnych (IIS). W związku z tym nie będzie działać na serwerze sieci web rozwoju. Aby profilować witrynę sieci Web w teście obciążenia, należy zainstalować agenta testowego na komputerze, na którym działa usługi IIS. Agent testowy nie będzie generował obciążenia, a jedynie pośredniczył w zbieraniu danych. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie ustawienia testu dla testu obciążenia rozproszonego](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Konfigurowanie ASP.NET profiler dla ustawień testowych

Przed wykonaniem kroków w tej procedurze, należy otworzyć ustawienia testu z programu Visual Studio i wybierz **dane i diagnostyki** strony.

1. Wybierz rolę, która ma być używana do zbierania danych ASP.NET profilera.

    > [!WARNING]
    > Ta rola musi być serwerem sieci web.

2. Wybierz **ASP.NET Profilera,** aby włączyć zbieranie danych profilowania ASP.NET, a następnie wybierz pozycję **Konfiguruj**.

     Zostanie wyświetlone okno dialogowe do konfigurowania ASP.NET profilowania danych.

3. W **interwał próbkowania profilera**wpisz wartość, która wskazuje, ile cykli zegara procesora CPU nie zatrzymał czekać między pobieraniem ASP.NET profilowania próbek.

4. Aby włączyć profilowanie interakcji warstwy, wybierz pozycję **Włącz profilowanie interakcji warstwy**.

     Profilowanie interakcji warstwy zlicza liczbę żądań wysyłanych do serwera sieci web dla każdego artefaktu (na przykład *MyPage.aspx* lub *CompanyLogo.gif)* i czas, jaki zajęło obsługę każdego żądania. Ponadto są zbierane informacje o tym, które połączenia środowiska ADO.NET były używane w ramach żądania o stronę oraz jak wiele zapytań i wywołań procedur przechowywanych zostało wykonanych w ramach obsługi tego żądania.

     Mechanizm zbiera dwa różne zestawy informacji o czasie:

    - Informacje o czasie (Min., Maks., Średnia i Suma) obsługi każdego żądania sieci web.

    - Informacje o czasie (Min., Maks., Średnia i Suma) wykonania każdego zapytania.

Dzięki karcie danych diagnostycznych ASP.NET profilera skonfigurowanym w ustawieniu testowym można teraz zbierać dane ASP.NET profilowania w aplikacji sieci web ASP.NET.

## <a name="see-also"></a>Zobacz też

- [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Jak: Tworzenie ustawienia testu dla testu obciążenia rozproszonego](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)