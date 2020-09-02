---
title: 'Instrukcje: korzystanie z okna modułów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696126"
---
# <a name="how-to-use-the-modules-window"></a>Porady: korzystanie z okna modułów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KORYGUJĄC
> Ta funkcja jest niedostępna w przypadku debugowania SQL lub skryptów.  
  
 Okno **moduły** zawiera listę bibliotek DLL i exe, które są używane przez program, i wyświetla odpowiednie informacje dla każdego z nich.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Aby wyświetlić okno moduły w trybie przerwania lub w trybie uruchamiania  
  
- W menu **debugowanie** wybierz opcję **Windows**, a następnie kliknij pozycję **moduły**.  
  
     Domyślnie okno **moduły** sortuje moduły według kolejności ładowania. Można jednak wybrać sortowanie według dowolnej kolumny.  
  
### <a name="to-sort-by-any-column"></a>Aby posortować według dowolnej kolumny  
  
- Kliknij przycisk w górnej części kolumny.  
  
     Możesz załadować symbole lub określić ścieżkę symboli z okna **modułów** przy użyciu menu skrótów.  
  
## <a name="loading-symbols"></a>Ładowanie symboli  
 W oknie **moduły** można sprawdzić, które moduły mają załadowane symbole debugowania. Te informacje są wyświetlane w kolumnie **stan symbolu** . Jeśli stan ma wartość **pominięte loadingCannot Znajdź lub Otwórz plik PDB**lub Załaduj **wyłączone przez ustawienie Uwzględnij/Wyklucz**, można skierować debuger do pobrania symboli z publicznych serwerów symboli firmy Microsoft lub załadować symbole z katalogu symboli na komputerze. Aby uzyskać więcej informacji, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Aby załadować symbole ręcznie  
  
1. W oknie **moduły** kliknij prawym przyciskiem myszy moduł, dla którego symbole nie zostały załadowane.  
  
2. Wskaż **Załaduj symbole z** , a następnie kliknij pozycję **serwery symboli Microsoft** lub **ścieżka symboli**.  
  
#### <a name="to-change-symbol-load-settings"></a>Aby zmienić ustawienia ładowania symboli  
  
1. W oknie **moduły** kliknij prawym przyciskiem myszy dowolny moduł.  
  
2. Kliknij pozycję **Ustawienia symboli**.  
  
     Teraz można zmienić ustawienia ładowania symboli, zgodnie z opisem w temacie [Określanie lokalizacji symboli i zachowanie ładowania](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Zmiany zaczną obowiązywać dopiero po ponownym uruchomieniu sesji debugowania.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Aby zmienić zachowanie ładowania symboli dla określonego modułu  
  
1. W oknie **moduły** kliknij prawym przyciskiem myszy moduł.  
  
2. Wskaż **Opcje automatyczne ładowanie symboli** , a następnie kliknij opcję **Zawsze ładuj ręcznie** lub **domyślną**. Zmiany zaczną obowiązywać dopiero po ponownym uruchomieniu sesji debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przerywanie wykonywania](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
