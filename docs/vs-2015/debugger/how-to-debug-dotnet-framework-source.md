---
title: 'Instrukcje: debugowanie .NET Framework Źródło | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205446"
---
# <a name="how-to-debug-net-framework-source"></a>Porady: debugowanie źródła .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowsza wersja programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] udostępnia nowe funkcje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] debugowania. Aby debugować [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Źródło, musisz mieć dostęp do symboli debugowania dla kodu. Należy również włączyć przechodzenie do kodu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] źródłowego.  
  
 Możesz włączyć [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] krokowe i pobieranie symboli w oknie dialogowym **Opcje** . Po włączeniu pobierania symboli możesz natychmiast pobrać symbole lub po prostu włączyć opcję w celu późniejszego pobrania. Jeśli nie pobierzesz symboli natychmiast, symbole zostaną pobrane przy następnym uruchomieniu debugowania aplikacji. Możesz również ręcznie pobrać z okna **moduły** lub z okna **stosu wywołań** .  
  
### <a name="to-enable-net-framework-source-debugging"></a>Aby włączyć debugowanie źródła .NET Framework  
  
1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).  
  
2. W oknie dialogowym **Opcje** kliknij kategorię **debugowanie** .  
  
3. W polu **Ogólne** ustaw opcję Włącz wykonywanie kroków źródłowych **.NET Framework** .  
  
    1. Jeśli Tylko mój kod włączone, okno dialogowe ostrzeżenia informuje, że Tylko mój kod jest teraz wyłączone. Kliknij przycisk **OK**.  
  
    2. Jeśli nie masz ustawionej lokalizacji pamięci podręcznej symboli, inne okno dialogowe ostrzeżenia informuje, że jest teraz ustawiona domyślna lokalizacja pamięci podręcznej symboli. Kliknij przycisk **OK**.  
  
4. W kategorii **debugowanie** kliknij pozycję **symbole**.  
  
5. Jeśli chcesz zmienić lokalizację pamięci podręcznej symboli:  
  
    1. Otwórz węzeł **debugowanie** w polu po lewej stronie.  
  
    2. W węźle **debugowanie** kliknij pozycję **symbole**.  
  
    3. Edytuj lokalizację w **symbolach pamięci podręcznej z serwerów symboli w tym katalogu** lub kliknij przycisk **Przeglądaj** , aby wybrać lokalizację.  
  
6. Jeśli chcesz pobrać symbole natychmiast, kliknij przycisk **Wczytaj symbole przy użyciu powyższych lokalizacji**.  
  
     Ten przycisk nie jest dostępny w trybie projektowania.  
  
     Jeśli nie zdecydujesz się na pobieranie symboli teraz, symbole zostaną pobrane automatycznie przy następnym uruchomieniu debugowania programu.  
  
7. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Opcje** .  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Aby załadować symbole struktury przy użyciu okna moduły  
  
1. W oknie **moduły** kliknij prawym przyciskiem myszy moduł, dla którego symbole nie są ładowane. Można określić, czy symbole są ładowane, czy nie, patrząc na kolumnę **Stan symboli** .  
  
2. Wskaż **Załaduj symbole z** i kliknij pozycję **serwery symboli firmy Microsoft** , aby pobrać symbole z serwera Microsoft Public Symbols lub **ścieżki symboli** , które mają zostać załadowane z katalogu, w którym wcześniej przechowywane zostały symbole.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Aby załadować symbole struktury przy użyciu okna stosu wywołań  
  
1. W oknie **stos wywołań** kliknij prawym przyciskiem myszy ramkę, dla której symbole nie są ładowane. Ramka będzie wyszarzona.  
  
2. Wskaż **Załaduj symbole z** i kliknij pozycję **serwery symboli firmy Microsoft** lub **ścieżka symboli**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
