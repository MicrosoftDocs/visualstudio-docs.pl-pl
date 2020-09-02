---
title: Odinstalowywanie programu Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ed9d33501644c6fa7252dffa758f92c0919653b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546905"
---
# <a name="uninstall-visual-studio"></a>Odinstalowywanie programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [Odinstalowywanie programu Visual Studio](/visualstudio/install/uninstall-visual-studio).

Ta strona przeprowadzi Cię przez proces odinstalowywania programu Visual Studio 2015, wcześniejszej wersji naszego zintegrowanego pakietu narzędzi zwiększających produktywność dla deweloperów.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Odinstalowywanie programu Visual Studio przy użyciu "standardowej" metody odinstalowywania

1. W **Panelu sterowania**na stronie **programy i funkcje** wybierz wersję produktu, którą chcesz odinstalować, a następnie wybierz pozycję **Zmień**.

2. W Kreatorze instalacji wybierz **Odinstaluj**, wybierz **tak**, a następnie postępuj zgodnie z instrukcjami wyświetlanymi w kreatorze.

   Ta standardowa, czyli domyślna, Metoda pozostawi pewne elementy po pierwszej instalacji programu Visual Studio (na przykład Microsoft .NET Framework, Microsoft Visual C++ redystrybucyjne, Microsoft SQL Server itd.).   Pozostałe aplikacje są opuszczane, ponieważ zależą od nich wiele innych aplikacji. Jeśli jednak chcesz je usunąć, wybierz ich wpis w **aplecie Programy i funkcje**, a następnie usuń każdy z nich osobno.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Odinstaluj program Visual Studio i wszystkie inne powiązane pliki (oznacza to, aby odinstalować niemal wszystko)

1. Znajdź plik programu Visual Studio. exe (na przykład Znajdź "vs_enterprise.exe").

    > [!NOTE]
    > Plik powinien znajdować się w podfolderze "Cache%ProgramData%\Package", na przykład: C:\ProgramData\Package cache \\ {37e19555-e88d-4aed-9d42-82d0784d2b79} \vs_enterprise.exe

2. Uruchom plik exe przy użyciu parametrów wiersza polecenia/Uninstall/Force.

     Na przykład uruchom ```vs_enterprise.exe /uninstall /force``` polecenie, które spowoduje usunięcie programu Visual Studio i większości podstawowych składników, które są pozostawione w domyślnej dezinstalacji. Nie spowoduje to jednak usunięcia całej dodatkowej zawartości, którą mogą instalować dodatki i rozszerzenia programu Visual Studio (na przykład aktualizacje programu Visual Studio i inne składniki opcjonalne).

    > [!TIP]
    > Alternatywnie można użyć narzędzia "**Total dezinstalatora**", aby usunąć wszystkie elementy, które mogą zostać zainstalowane przez program Visual Studio lub aktualizacje programu Visual Studio. Oznacza to, że dowolna wersja Visual Studio 2013 lub nowsza. Aby dowiedzieć się więcej, zobacz [Narzędzie Visual Studio dezinstalatora](https://github.com/Microsoft/VisualStudioUninstaller/releases) w witrynie GitHub.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Odinstaluj program Visual Studio w trybie cichym lub pasywnym (czyli w celu odinstalowania ze źródła)

1. Na komputerze, na którym jest zainstalowany program Visual Studio, otwórz wiersz polecenia systemu Windows.

2. Wprowadź następujące parametry:

     *DVDRoot* \\ Plik instalacyjny<\> \</quiet&#124;/passive> [/norestart]/Uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Przywracanie poprzedniej wersji lub wydania programu Visual Studio

1. Odinstaluj program Visual Studio, używając dowolnej metody wymienionej w tym temacie.

   > [!WARNING]
   > Odinstalowanie bieżącej wersji programu Visual Studio (lub aktualizacji programu Visual Studio), a następnie zainstalowanie wcześniejszej wersji może nie zadziałała zgodnie z oczekiwaniami.
   >
   > Wyniki są zależne od wersji lub wydania programu Visual Studio, które wersje jego składników są zainstalowane, które produkty są zainstalowane, które mogą być zależne od wersji programu Visual Studio lub jej składników, a na koniec, na której wcześniejsza wersja programu Visual Studio jest zaplanowana do zainstalowania lub ponownego zainstalowania.  Ze względu na wszystkie te zmienne, standardowa Dezinstalacja często opuszcza składniki, które mogą nie współpracować z poprzednimi wersjami lub wydaniami programu Visual Studio.
   >
   > Dlatego w celu uzyskania najlepszych wyników zalecamy korzystanie z [narzędzia Visual Studio dezinstalatora](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Zainstaluj lub ponownie zainstaluj starszą wersję programu Visual Studio, której chcesz użyć.

   Nawet jeśli zainstalujesz poprzednią wersję programu Visual Studio, program instalacyjny może nadal próbować użyć nowszej wersji lub wydania, jeśli jest dostępny. Aby uzyskać bardziej szczegółowe informacje, zobacz temat [How to: Install a określonej wersji programu Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md) .

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)