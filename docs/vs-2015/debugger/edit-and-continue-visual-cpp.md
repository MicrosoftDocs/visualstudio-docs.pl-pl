---
title: Edytuj i Kontynuuj (Visual C++) | Microsoft Docs
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
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef02f08ac635687eaaf071188ba0455c6389d9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301058"
---
# <a name="edit-and-continue-visual-c"></a>Edytuj i kontynuuj (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć Edytuj i Kontynuuj w projektach Visual C++. Zobacz [obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md) , aby uzyskać informacje o ograniczeniach Edytuj i Kontynuuj.  
  
 Począwszy od programu Visual Studio 2015 Update 1, można teraz używać opcji Edytuj i Kontynuuj w aplikacjach Windows Store w języku C++ i aplikacjach DirectX, ponieważ teraz obsługuje przełącznik kompilatora **/Zi** z przełącznikiem **/bigobj** . Można również użyć opcji Edytuj i Kontynuuj z plikami binarnymi skompilowanymi przy użyciu przełącznika **/Fastlink** .  
  
 Inne ulepszenia Update 1 obejmują nowe, anulowane okno dialogowe oczekiwania i powiadomienia, gdy plik nie obsługuje funkcji Edytuj i Kontynuuj. Aby uzyskać więcej informacji na temat ulepszeń Update 1, zobacz [ulepszenia języka C++ Edytuj i Kontynuuj w programie Visual Studio 2015 Update 1](https://devblogs.microsoft.com/cppblog/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1/).  
  
 Opcja kompilatora [/zo (rozszerzanie zoptymalizowanego debugowania)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) wprowadzona w Visual Studio 2013 Update 3 dodaje dodatkowe informacje do plików. pdb (symbol), które zostały skompilowane bez [/od (Disable (Debug))](https://msdn.microsoft.com/library/aafb762y.aspx) .  
  
 **/Zo** wyłącza funkcję Edytuj i Kontynuuj. Zobacz [jak: debugowanie zoptymalizowanego kodu](../debugger/how-to-debug-optimized-code.md).  
  
## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Włącz lub wyłącz opcję Edytuj i Kontynuuj  
 Można wyłączyć automatyczne wywoływanie operacji Edytuj i Kontynuuj, jeśli wprowadzasz zmiany w kodzie, który nie ma być stosowany podczas bieżącej sesji debugowania. Możesz również ponownie włączyć automatyczne edytowanie i kontynuowanie.  
  
1. W menu **Narzędzia** wybierz polecenie **Opcje**.  
  
2. W oknie dialogowym **Opcje** wybierz pozycję **debugowanie/ogólne**.  
  
3. W grupie **Edytuj i Kontynuuj** zaznacz lub wyczyść pole wyboru **Włącz natywne edytowanie i kontynuowanie** .  
  
   Zmiana tego ustawienia ma wpływ na wszystkie projekty, nad którymi pracujesz. Po zmianie tego ustawienia nie trzeba ponownie kompilować aplikacji. Można zmienić to ustawienie nawet podczas debugowania. W przypadku kompilowania aplikacji z poziomu wiersza polecenia lub pliku reguł programu make, ale w środowisku programu Visual Studio można nadal używać opcji Edytuj i Kontynuuj, jeśli ustawisz opcję **/Zi** .  
  
## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> Jak jawnie zastosować zmiany kodu  
 W Visual C++ Edytuj i Kontynuuj mogą zastosować zmiany kodu na dwa sposoby. Zmiany kodu można zastosować niejawnie, po wybraniu polecenia wykonywania lub jawnie przy użyciu polecenia **Zastosuj zmiany kodu** .  
  
 W przypadku jawnego stosowania zmian kodu program pozostaje w trybie przerwania — żadne wykonanie nie jest wykonywane.  
  
- Aby jawnie zastosować zmiany kodu, w menu **debugowanie** wybierz **Zastosuj zmiany kodu**.  
  
## <a name="how-to-stop-code-changes"></a><a name="BKMK_How_to_stop_code_changes"></a> Jak zatrzymać zmiany kodu  
 Podczas gdy Edytuj i Kontynuuj jest w trakcie stosowania zmian kodu, możesz zatrzymać operację.  
  
 Aby zatrzymać stosowanie zmian kodu:  
  
- Z menu **Debuguj** wybierz polecenie **Zatrzymaj stosowanie zmian kodu**.  
  
  Ten element menu jest widoczny tylko w przypadku stosowania zmian kodu.  
  
  W przypadku wybrania tej opcji nie są zatwierdzane żadne zmiany w kodzie.  
  
## <a name="how-to-reset-the-point-of-execution"></a><a name="BKMK_How_to_reset_the_point_of_execution"></a> Jak zresetować punkt wykonywania  
 Niektóre zmiany w kodzie mogą spowodować przechodzenie do nowej lokalizacji w momencie, gdy Edycja i kontynuowanie stosuje zmiany. Polecenie Edytuj i Kontynuuj umieszcza punkt wykonania jak dokładnie tak, jak jest to możliwe, ale wyniki mogą nie być poprawne we wszystkich przypadkach.  
  
 W Visual C++ okno dialogowe informuje o wprowadzeniu zmian w punkcie wykonania. Przed kontynuowaniem debugowania należy sprawdzić, czy lokalizacja jest poprawna. Jeśli nie jest poprawna, użyj polecenia **Set Next instrukcji** . Aby uzyskać więcej informacji, zobacz [Ustawianie następnej instrukcji do wykonania](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> Jak korzystać z nieodświeżonego kodu  
 W niektórych przypadkach polecenie Edytuj i Kontynuuj nie może natychmiast zastosować zmian kodu do pliku wykonywalnego, ale może być możliwe zastosowanie zmian kodu później w przypadku kontynuowania debugowania. Dzieje się tak, Jeśli edytujesz funkcję, która wywołuje bieżącą funkcję, lub jeśli dodasz więcej niż 64 bajtów nowych zmiennych do funkcji na stosie wywołań  
  
 W takich przypadkach Debuger kontynuuje wykonywanie oryginalnego kodu do momentu zastosowania zmian. Nieodświeżony kod pojawia się jako tymczasowe okno pliku źródłowego w osobnym oknie źródłowym, z tytułem takim jak `enc25.tmp` . Edytowane Źródło nadal pojawia się w oryginalnym oknie źródłowym. Jeśli spróbujesz edytować nieodświeżony kod, zostanie wyświetlony komunikat ostrzegawczy.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md)
