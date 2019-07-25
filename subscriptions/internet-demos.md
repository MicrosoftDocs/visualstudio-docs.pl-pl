---
title: Korzystanie z kluczy produktów do obsługi pokazów internetowych za pośrednictwem usług terminalowych | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Dowiedz się, jak używać kluczy produktów do obsługi pokazów internetowych za pośrednictwem usług terminalowych i włączania dostępu RDS
ms.openlocfilehash: 19faa64b7eeaebc1b92ca965f686795b31e00e7e
ms.sourcegitcommit: 9fc8b144d4ed1c46aba87c0b7e1d24454e0eea9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68493385"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Pokazy internetowe za pośrednictwem usług terminalowych
Za pomocą subskrypcji programu Visual Studio możesz zapewnić użytkownikom końcowym dostęp do pokazów internetowych programów za pośrednictwem usług terminalowych (Windows Server 2003 lub Windows Server 2008) lub Usługi pulpitu zdalnego (system Windows Server 2008 R2 i nowsze). Do 200 anonimowych użytkowników może jednocześnie uzyskać dostęp do demonstracji w ten sposób. Demonstracja nie może korzystać z danych produkcyjnych. Subskrybenci programu Visual Studio mają licencję na prezentowanie aplikacji użytkownikom końcowym. Ta prezentacja internetowa korzystająca z usług terminalowych lub Usługi pulpitu zdalnego (RDS) jest jedynym scenariuszem, w którym użytkownicy końcowi bez subskrypcji programu Visual Studio mogą korzystać z aplikacji demonstracyjnej, gdy oprogramowanie jest licencjonowane za pośrednictwem wizualizacji Subskrypcje Studio.

Jest to uzupełnienie praw deweloperskich/testowych, w przypadku których Subskrybenci programu Visual Studio mogą używać jako wielu połączeń usług pulpitu zdalnego lub usług terminalowych.

## <a name="enabling-rds-access"></a>Włączanie dostępu RDS
Subskrybenci programu Visual Studio mogą zwiększyć liczbę użytkowników, którzy mogą uzyskać dostęp do systemu Windows Server za pośrednictwem usług RDS, wprowadzając klucz produktu dostarczony na karcie [klucze produktu](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) w [portalu subskrybenta](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Aby uzyskać klucz produktu, Połącz się ze stroną klucze produktu i przewiń w dół do używanej wersji systemu Windows Server. Znajdź pozycję "Windows Server < version > R2 Usługi pulpitu zdalnego < połączenia użytkowników lub urządzeń >" i kliknij link **klucz roszczeń** . Jeśli na przykład używasz usług pulpitu zdalnego w systemie Windows Server 2012 R2, a wdrożenie korzysta z licencji CAL użytkownika, wybierz pozycję "Windows Server 2012 Usługi pulpitu zdalnego połączenia użytkowników (50)".
Dla systemu Windows Server 2008 R2 dostępne są pięć kluczy każdego typu, a każdy klucz będzie obsługiwał 20 połączeń. W przypadku systemu Windows Server 2012 R2 cztery klucze dla każdego typu są zapewniane i będą obsługiwały 50 połączeń każdego z nich.

## <a name="to-enable-additional-connections-in-windows-server"></a>Aby włączyć dodatkowe połączenia w systemie Windows Server:
1. Otwórz Menedżera serwera.
2. Otwórz listę serwery w okienku nawigacji po lewej stronie.
3. Kliknij prawym przyciskiem myszy serwer licencji i wybierz polecenie "Zainstaluj licencje".
4. Postępuj zgodnie z instrukcjami wyświetlanymi w kreatorze.  Po wybraniu typu umowy wybierz pozycję "pakiet licencji (detaliczna)" i wprowadź klucz produktu uzyskany w portalu.

Użytkownicy końcowi mogą łączyć się z dostępem do aplikacji za pośrednictwem usług pulpitu zdalnego, jeśli są spełnione następujące warunki:
- Użytkownicy muszą być anonimowi (w stanie nieuwierzytelnionym).
- Połączenia muszą należeć przez Internet.
- W celu pokazania aplikacji można używać maksymalnie 200 połączeń użytkownika.
- Klucze produktów umożliwiające nawiązywanie połączeń użytkowników muszą zostać uzyskane przez subskrybenta programu Visual Studio.

## <a name="next-steps"></a>Następne kroki
Jeśli potrzebujesz wskazówek dotyczących wdrażania usług pulpitu zdalnego, zapoznaj się z wieloczęściową serią w blogu dotyczącą **wdrożenia sesji programu usługi pulpitu zdalnego (RDS) 2012** na stronie https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf. 

Jeśli masz jakieś pytania, odwiedź [forum usług pulpit zdalny Microsoft Services](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS).
