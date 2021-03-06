---
title: Edytuj i Kontynuuj (C++) | Microsoft Docs
description: Edytuj i Kontynuuj jest dostępny dla projektów C++. Dowiedz się, jakie zmiany są obsługiwane i jak można kontrolować, czy są stosowane zmiany.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 0c4fd6d5214211318e2271418425a117a73eb0ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871887"
---
# <a name="edit-and-continue-c"></a>Edytuj i kontynuuj (C++)
Możesz użyć Edytuj i Kontynuuj w projektach języka C++. Zobacz [obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md) , aby uzyskać informacje o ograniczeniach Edytuj i Kontynuuj.

Aby uzyskać więcej informacji na temat ulepszeń programu Visual Studio 2015 Update 3, zobacz [C++ Edytuj i Kontynuuj w programie Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 Opcja kompilatora [/zo (rozszerzanie zoptymalizowanego debugowania)](/cpp/build/reference/zo-enhance-optimized-debugging) wprowadzona w Visual Studio 2013 Update 3 dodaje dodatkowe informacje do plików. pdb (symbol), które zostały skompilowane bez [/od (Disable (Debug))](/cpp/build/reference/od-disable-debug) .

 **/Zo** wyłącza funkcję Edytuj i Kontynuuj. Zobacz [jak: debugowanie zoptymalizowanego kodu](../debugger/how-to-debug-optimized-code.md).

## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Włącz lub wyłącz opcję Edytuj i Kontynuuj
 Można wyłączyć automatyczne wywoływanie operacji Edytuj i Kontynuuj, jeśli wprowadzasz zmiany w kodzie, który nie ma być stosowany podczas bieżącej sesji debugowania. Możesz również ponownie włączyć automatyczne edytowanie i kontynuowanie.

> [!IMPORTANT]
> Aby uzyskać wymagane ustawienia kompilacji i inne informacje dotyczące zgodności funkcji, zobacz [C++ Edytuj i Kontynuuj w programie Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Jeśli jesteś w sesji debugowania, Zatrzymaj debugowanie (**Shift + F5**).

2. W menu **Narzędzia** wybierz polecenie **Opcje**.

3. W oknie dialogowym **Opcje** wybierz pozycję **debugowanie > ogólne**.

4. Aby włączyć, wybierz pozycję **Włącz Edytuj i Kontynuuj**. Aby wyłączyć, wyczyść pole wyboru.

5. W grupie **Edytuj i Kontynuuj** zaznacz lub wyczyść pole wyboru **Włącz natywne edytowanie i kontynuowanie** .

   Zmiana tego ustawienia ma wpływ na wszystkie projekty, nad którymi pracujesz. Po zmianie tego ustawienia nie trzeba ponownie kompilować aplikacji. W przypadku kompilowania aplikacji z poziomu wiersza polecenia lub pliku reguł programu make, ale w środowisku programu Visual Studio można nadal używać opcji Edytuj i Kontynuuj, jeśli ustawisz opcję **/Zi** .

## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> Jak jawnie zastosować zmiany kodu
 W języku C++ Edycja i kontynuacja mogą stosować zmiany kodu na dwa sposoby. Zmiany kodu można zastosować niejawnie, po wybraniu polecenia wykonywania lub jawnie przy użyciu polecenia **Zastosuj zmiany kodu** .

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

 W języku C++ okno dialogowe informuje o wprowadzeniu zmian w punkcie wykonania. Przed kontynuowaniem debugowania należy sprawdzić, czy lokalizacja jest poprawna. Jeśli nie jest poprawna, użyj polecenia **Set Next instrukcji** . Aby uzyskać więcej informacji, zobacz [Ustawianie następnej instrukcji do wykonania](./navigating-through-code-with-the-debugger.md#BKMK_Set_the_next_statement_to_execute).

## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> Jak korzystać z nieodświeżonego kodu
 W niektórych przypadkach polecenie Edytuj i Kontynuuj nie może natychmiast zastosować zmian kodu do pliku wykonywalnego, ale może być możliwe zastosowanie zmian kodu później w przypadku kontynuowania debugowania. Dzieje się tak, Jeśli edytujesz funkcję, która wywołuje bieżącą funkcję, lub jeśli dodasz więcej niż 64 bajtów nowych zmiennych do funkcji na stosie wywołań

 W takich przypadkach Debuger kontynuuje wykonywanie oryginalnego kodu do momentu zastosowania zmian. Nieodświeżony kod pojawia się jako tymczasowe okno pliku źródłowego w osobnym oknie źródłowym, z tytułem takim jak `enc25.tmp` . Edytowane Źródło nadal pojawia się w oryginalnym oknie źródłowym. Jeśli spróbujesz edytować nieodświeżony kod, zostanie wyświetlony komunikat ostrzegawczy.

## <a name="see-also"></a>Zobacz też
- [Obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md)