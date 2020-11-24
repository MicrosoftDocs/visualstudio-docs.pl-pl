---
title: Konfigurowanie profilera ASP.NET dla testów obciążenia
description: Dowiedz się, jak zbierać informacje profilera ASP.NET przy użyciu adaptera danych diagnostycznych ASP.NET Profiler.
ms.custom: SEO-VS-2020
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: baea8be1da9a6dd89c06aa328bf579974503921f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442329"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Instrukcje: Konfigurowanie profilera ASP.NET na potrzeby testów obciążenia przy użyciu ustawień testu w programie Visual Studio

Za pomocą adaptera danych diagnostycznych profilera ASP.NET można zbierać informacje o profilerze ASP.NET. Ten adapter danych diagnostycznych zbiera dane o wydajności dla aplikacji ASP.NET.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Nie można użyć tego adaptera danych diagnostycznych dla testów, które są uruchamiane za pomocą Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). Możesz użyć karty diagnostycznej profilera ASP.NET z testami obciążenia tylko przy użyciu witryn sieci Web, które wymagają Visual Studio Enterprise.

Adapter danych diagnostycznych profilera ASP.NET umożliwia zbieranie danych profilera ASP.NET z warstwy aplikacji podczas uruchamiania testu obciążenia. Profilera nie należy uruchamiać dla długich testów obciążeniowych, na przykład trwających ponad godzinę. Wynika to z faktu, że plik profilera może się rozrosnąć, nawet do kilkuset megabajtów. Zamiast tego należy uruchamiać krótsze testy obciążenia przy użyciu profilera ASP.NET, co zapewnia korzyści wynikające z dokładnej diagnostyki problemów z wydajnością.

> [!NOTE]
> Profil adaptera danych diagnostycznych profilera programu ASP.NET w procesie Internet Information Services (IIS). W związku z tym nie będzie on działał na deweloperskim serwerze sieci Web. Aby profilować witrynę sieci Web w teście obciążenia, należy zainstalować agenta testowego na komputerze, na którym są uruchomione usługi IIS. Agent testowy nie będzie generował obciążenia, a jedynie pośredniczył w zbieraniu danych. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

Aby uzyskać więcej informacji, zobacz [How to: Create a test setting for a Distributed Load test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Skonfiguruj Profiler ASP.NET dla ustawień testu

Przed wykonaniem kroków opisanych w tej procedurze należy otworzyć ustawienia testu w programie Visual Studio i wybrać stronę **dane i Diagnostyka** .

1. Wybierz rolę, która ma być używana do zbierania danych programu ASP.NET Profiler.

    > [!WARNING]
    > Ta rola musi być serwerem sieci Web.

2. Wybierz pozycję **ASP.NET Profiler** , aby włączyć zbieranie danych profilowania ASP.NET, a następnie wybierz pozycję **Konfiguruj**.

     Zostanie wyświetlone okno dialogowe umożliwiające skonfigurowanie zbierania danych profilowania ASP.NET.

3. W polu **Interwał próbkowania profilera** wpisz wartość wskazującą, ile niezatrzymanego zegara procesora CPU ma oczekiwać między pobieraniem ASP.NET profilowania.

4. Aby włączyć profilowanie interakcji między warstwami, wybierz pozycję **Włącz profilowanie interakcji między warstwami**.

     Profilowanie interakcji między warstwami zlicza liczbę żądań wysyłanych do serwera sieci Web dla każdego artefaktu (na przykład *webpage. aspx* lub *CompanyLogo.gif*) oraz czasu, jaki zajęło obsługę każdego żądania. Ponadto są zbierane informacje o tym, które połączenia środowiska ADO.NET były używane w ramach żądania o stronę oraz jak wiele zapytań i wywołań procedur przechowywanych zostało wykonanych w ramach obsługi tego żądania.

     Mechanizm zbiera dwa różne zestawy informacji o czasie:

    - Informacje o czasie (Min., Maks., Średnia i Suma) obsługi każdego żądania sieci web.

    - Informacje o czasie (Min., Maks., Średnia i Suma) wykonania każdego zapytania.

Za pomocą adaptera danych diagnostycznych profilera ASP.NET skonfigurowanych w ustawieniu testu możesz teraz zbierać dane profilowania ASP.NET w aplikacji sieci Web ASP.NET.

## <a name="see-also"></a>Zobacz także

- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Instrukcje: Tworzenie ustawień testowych dla testu obciążenia rozłożonego](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)