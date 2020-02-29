---
title: Konfigurowanie programu ASP.NET Profiler dla testów obciążenia
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0132401df33bd65d7e328307167b6c228155bb42
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169394"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Porady: Konfiguracja profilera ASP.NET do testów obciążenia za pomocą ustawienia testu w programie Visual Studio

Adapter danych diagnostycznych profilera ASP.NET służy do zbierania informacji z profilera środowiska ASP.NET. Ten adapter danych diagnostycznych zbiera dane wydajności dla aplikacji ASP.NET.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Nie można użyć tego adaptera danych diagnostycznych dla testów, które są uruchamiane przy użyciu programu Microsoft Test Manager. Możesz za pomocą adaptera diagnostycznego programu ASP.NET Profiler testów obciążenia za pomocą witryn sieci Web, która wymaga programu Visual Studio Enterprise.

Adapter danych diagnostycznych profilera ASP.NET umożliwia zbieranie danych profilera platformy ASP.NET z warstwy aplikacji, po uruchomieniu testu obciążenia. Profilera nie należy uruchamiać dla długich testów obciążeniowych, na przykład trwających ponad godzinę. Wynika to z faktu, że plik profilera może się rozrosnąć, nawet do kilkuset megabajtów. Zamiast tego należy wykonywać krótsze testy obciążeniowe przy użyciu profilera platformy ASP.NET, który wciąż daje korzyści też bardzo szczegółowo diagnozuje problemy z wydajnością.

> [!NOTE]
> Adapter danych diagnostycznych profilera ASP.NET profiluje proces Internet Information Services (IIS). W związku z tym nie będzie on działał dla serwera sieci web development. Profilowanie witryny sieci Web w teście obciążenia, musisz zainstalować agenta testowego na komputerze, na którym działa program IIS. Agent testowy nie będzie generował obciążenia, a jedynie pośredniczył w zbieraniu danych. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

Aby uzyskać więcej informacji, zobacz [How to: Create a test setting for a Distributed Load test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Konfiguracja profilera ASP.NET do ustawień testu

Przed wykonaniem kroków opisanych w tej procedurze należy otworzyć ustawienia testu w programie Visual Studio i wybrać stronę **dane i Diagnostyka** .

1. Wybierz rolę, która ma zbierać dane profilera platformy ASP.NET.

    > [!WARNING]
    > Ta rola musi być serwerem sieci web.

2. Wybierz pozycję **ASP.NET Profiler** , aby włączyć zbieranie danych profilowania ASP.NET, a następnie wybierz pozycję **Konfiguruj**.

     Wyświetlane jest okno dialogowe, aby skonfigurować zbieranie danych z profilowania ASP.NET.

3. W polu **Interwał próbkowania profilera**wpisz wartość wskazującą, ile niezatrzymanego zegara procesora CPU ma oczekiwać między pobieraniem ASP.NET profilowania.

4. Aby włączyć profilowanie interakcji między warstwami, wybierz pozycję **Włącz profilowanie interakcji między warstwami**.

     Profilowanie interakcji między warstwami zlicza liczbę żądań wysyłanych do serwera sieci Web dla każdego artefaktu (na przykład pliku *Web. aspx* lub *CompanyLogo. gif*) oraz czasu, jaki zajęło obsługę każdego żądania. Ponadto są zbierane informacje o tym, które połączenia środowiska ADO.NET były używane w ramach żądania o stronę oraz jak wiele zapytań i wywołań procedur przechowywanych zostało wykonanych w ramach obsługi tego żądania.

     Mechanizm zbiera dwa różne zestawy informacji o czasie:

    - Informacje o czasie (Min., Maks., Średnia i Suma) obsługi każdego żądania sieci web.

    - Informacje o czasie (Min., Maks., Średnia i Suma) wykonania każdego zapytania.

Adapter danych diagnostycznych profilera ASP.NET skonfigurowany w ustawieniach testu można teraz zbierać dane na aplikację sieci web platformy ASP.NET profilowania ASP.NET.

## <a name="see-also"></a>Zobacz też

- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Instrukcje: Tworzenie ustawień testowych dla testu obciążenia rozłożonego](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)