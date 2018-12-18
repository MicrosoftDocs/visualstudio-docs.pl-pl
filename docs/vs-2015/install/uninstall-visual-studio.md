---
title: Odinstaluj program Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 71e1318444c0b03ee5b2b9024c13bfbeb51b5c41
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050134"
---
# <a name="uninstall-visual-studio"></a>Odinstalowywanie programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio 2017, zobacz [Odinstalowywanie programu Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/uninstall-visual-studio).

Na tej stronie przeprowadzą odinstalowywania programu Visual Studio 2015 starszą wersję naszego zintegrowanego pakietu narzędzi zwiększających produktywność dla deweloperów.

##  <a name="uninstalling"></a>
#### <a name="to-uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Aby odinstalować program Visual Studio przy użyciu "standardowej" metody odinstalowywania

1. W **Panelu sterowania**na **programy i funkcje** wybierz wydanie produktu, który chcesz odinstalować, a następnie wybierz **zmiany**.

2. W Kreatorze instalacji wybierz **Odinstaluj**, wybierz **tak**, a następnie postępuj zgodnie z instrukcjami zawartymi w kreatorze.

   Ta standardowa, czyli domyślna, metoda pozostawi pewne elementy przez pierwszą instalację programu Visual Studio zainstalowane pierwotnie (na przykład program Microsoft .NET Framework, Microsoft pakiety redystrybucyjne Visual C++, program Microsoft SQL Server itp.).   Pozostawimy je zainstalować, ponieważ zależą od nich wiele innych aplikacji. Jednak jeśli chcesz je także usunąć, wybierz ich pozycje w **programy i funkcje**i Usuń każdy z nich osobno.

#### <a name="to-uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Aby odinstalować program Visual Studio i wszystkie powiązane pliki (czyli odinstalować prawie wszystko)

1.  Znajdź plik .exe programu Visual Studio (na przykład zlokalizuj "vs_enterprise.exe").

    > [!NOTE]
    >  Plik powinien znajdować się w podfolderze "%ProgramData%\Package Cache", na przykład: pamięć podręczna C:\ProgramData\Package\\\vs_enterprise.exe {37e19555-e88d-4aed-9d42-82d0784d2b79}

2.  Uruchom plik .exe, używając / uninstall/force parametry wiersza polecenia.

     Na przykład uruchomić ```vs_enterprise.exe /uninstall /force```, która spowoduje to usunięcie programu Visual Studio i większości podstawowych składników pozostawianych w przypadku dezinstalacji domyślnej. Jednak nie spowoduje to usunięcia całej dodatkowej zawartości tego dodatki programu Visual Studio i zainstalować rozszerzenia (na przykład aktualizacje programu Visual Studio i inne składniki opcjonalne).

    > [!TIP]
    > Alternatywnie, można użyć "**Total Uninstaller**" narzędzia, aby usunąć wszystkie elementy, że program Visual Studio lub mógł zainstalować aktualizacje programu Visual Studio. Oznacza to dowolnej wersji programu Visual Studio 2013 lub nowszej. Aby dowiedzieć się więcej, zobacz [dezinstalatora programu Visual Studio narzędzie](https://github.com/Microsoft/VisualStudioUninstaller/releases) w witrynie GitHub.

#### <a name="to-uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Aby odinstalować program Visual Studio w trybie cichym lub pasywnym (czyli odinstalować ze źródła)

1.  Na komputerze, na którym jest zainstalowany program Visual Studio, otwórz wiersz polecenia systemu Windows.

2.  Wprowadź następujące parametry:

     *DVDRoot* \\< plik instalacyjny\> \</quiet&#124;/passive > [/ norestart] / uninstall

#### <a name="to-roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Aby wrócić do poprzedniej wersji lub wydania programu Visual Studio

1. Odinstaluj program Visual Studio przy użyciu dowolnej metody wymienionej w tym temacie.

   > [!WARNING]
   >  Odinstalowanie aktualnego wydania programu Visual Studio (lub programu Visual Studio Update), a następnie zainstalowanie poprzedniego wydania może nie działać zgodnie z oczekiwaniami.
   >
   >  Wynik zależy od zainstalowanej wersji lub wydania programu Visual Studio został zainstalowany, które wersje jej składniki są zainstalowane, które produkty są zainstalowane mających zależności albo wersję programu Visual Studio lub jej składniki, a na koniec na które wcześniejszej wersji programu Visual Studio planujesz zainstalować lub ponownie zainstalować.  Z powodu tych wszystkich zmiennych standardowa Dezinstalacja są będzie często pozostawia składniki, które mogą nie działać z poprzednich wersji programu Visual Studio lub wersji.
   >
   >  W związku z tym, aby uzyskać najlepsze wyniki, zaleca się używanie [dezinstalatora programu Visual Studio narzędzie](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Zainstaluj lub ponownie zainstaluj starszą wersję programu Visual Studio, której chcesz użyć.

   Nawet wtedy, gdy możesz zainstalować poprzednią wersję programu Visual Studio, program instalacyjny może nadal próbować użyć nowszej wersji lub wydania, jeśli jest on dostępny. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie określonej wersji programu Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md) tematu.

## <a name="see-also"></a>Zobacz też
 [Instalowanie programu Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)