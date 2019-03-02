---
title: Edytuj i Kontynuuj (Visual C++) | Dokumentacja firmy Microsoft
ms.date: 05/31/2017
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3afb55c41f48c6d5e5a153c12cd364d130129d79
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222366"
---
# <a name="edit-and-continue-visual-c"></a>Edytuj i kontynuuj (Visual C++)
W projektach języka Visual C++ można użyć Edytuj i Kontynuuj. Zobacz [obsługiwane zmiany kodu (C++, Distributed File System)](../debugger/supported-code-changes-cpp.md) informacji o ograniczeniach operacji Edytuj i Kontynuuj.

Aby uzyskać więcej informacji na temat ulepszenia programu Visual Studio 2015 Update 3, zobacz [C++ Edytuj i Kontynuuj w Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 [/Zo (Rozszerzanie zoptymalizowane pod kątem debugowanie)](/cpp/build/reference/zo-enhance-optimized-debugging) opcję kompilatora, która została wprowadzona w Visual Studio 2013 Update 3 dodaje dodatkowe informacje w plikach .pdb (symbol) dla danych binarnych skompilowany bez [/Od (Wyłącz (Debuguj)) ](https://msdn.microsoft.com/library/aafb762y.aspx) opcji.

 **/ZO** wyłącza Edytuj i Kontynuuj. Zobacz [jak: Debugowanie zoptymalizowanego kodu](../debugger/how-to-debug-optimized-code.md).

##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Włączanie lub wyłączanie funkcji Edytuj i Kontynuuj
 Można wyłączyć automatycznego wywołania opcji Edytuj i Kontynuuj, jeśli jest wprowadzanie zmian do kodu, który ma zostać zastosowane podczas bieżącej sesji debugowania. Możesz też ponownie włączyć automatyczne Edytuj i Kontynuuj.

> [!IMPORTANT]
> Ustawienia kompilacji wymagane i inne informacje dotyczące zgodności z funkcji, zobacz [C++ Edytuj i Kontynuuj w Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Jeśli jesteś w sesji debugowania, Zatrzymaj debugowanie (**Shift + F5**).

2. Na **narzędzia** menu, wybierz **opcje**.

3. W **opcje** okno dialogowe, wybierz opcję **debugowanie > Ogólne**.

4. Aby włączyć, wybierz **Włącz edytowanie i kontynuowanie**. Aby wyłączyć, usuń zaznaczenie pola wyboru.

5. W **Edytuj i Kontynuuj** grupy, zaznacz lub wyczyść **Włączanie natywnego Edytuj i Kontynuuj** pole wyboru.

   Zmieniając to ustawienie ma wpływ na wszystkie projekty, którą pracujesz. Nie trzeba ponownie skompiluj aplikację po zmianie tego ustawienia. Jeśli kompilujesz aplikację z poziomu wiersza polecenia lub pliku reguł programu make, ale debugowanie w środowisku Visual Studio, nadal można Edytuj i Kontynuuj po ustawieniu **/zi** opcji.

##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Jak jawne stosowanie zmian kodu
 W programie Visual C++ Edytuj i Kontynuuj można zastosować zmian w kodzie na dwa sposoby. Kod można zastosować zmian niejawnie, wybierając polecenie wykonania, lub jawnie przy użyciu **zastosowanie zmian kodu** polecenia.

 Gdy jawne stosowanie zmian kodu programu pozostaje w trybie przerwania — nie jest wykonywany.

-   Aby zastosować zmiany w kodzie jawnie, na **debugowania** menu, wybierz **zastosowanie zmian kodu**.

##  <a name="BKMK_How_to_stop_code_changes"></a> Jak zatrzymywanie zmian kodu
 Gdy Edytuj i Kontynuuj Trwa stosowanie zmian kodu, można zatrzymać operacji.

 Aby zatrzymać, stosowanie zmian kodu:

- Na **debugowania** menu, wybierz **Zatrzymaj stosowanie zmian kodu**.

  Ten element menu jest widoczny tylko wtedy, gdy zmiany kodu są stosowane.

  Jeśli ta opcja jest wybrana, żadne zmiany kodu są zatwierdzone.

##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> Jak zresetować punkty wykonywania
 Niektóre zmiany kodu mogą spowodować punkt wykonywania, aby przejść do nowej lokalizacji, gdy Edytuj i Kontynuuj stosuje te zmiany. Edytuj i Kontynuuj umieszcza punkt wykonania jak to możliwe, ale wyniki mogą być niepoprawne we wszystkich przypadkach.

 W programie Visual C++ okno dialogowe informuje użytkownika, podczas zmiany punktów wykonywania. Należy sprawdzić czy lokalizacja jest poprawna, przed kontynuowaniem debugowania. Jeśli nie jest poprawny, należy użyć **Ustaw następną instrukcję** polecenia. Aby uzyskać więcej informacji, zobacz [Ustaw następną instrukcję do wykonania](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).

##  <a name="BKMK_How_to_work_with_stale_code"></a> Jak pracować z kodem nieodświeżonym
 W niektórych przypadkach Edytuj i Kontynuuj nie można od razu zastosować zmiany kodu do pliku wykonywalnego, ale można zastosować zmian w kodzie później, jeśli będziesz kontynuować debugowanie. Dzieje się tak w przypadku edycji funkcji wywołującej bieżącą funkcję, lub jeśli dodasz więcej niż 64 bajtów zmiennych nowych funkcji w stosie wywołań

 W takich przypadkach Debuger kontynuuje wykonywanie oryginalny kod, dopóki nie można zastosować zmiany. Nieodświeżony kod jest wyświetlany jako okno pliku tymczasowego źródła, w oknie oddzielne źródło, z tytułem takich jak `enc25.tmp`. Źródło edytowanych w dalszym ciągu są wyświetlane w oknie oryginalnego źródła. Jeśli spróbujesz edytować nieodświeżonego kodu, zostanie wyświetlony komunikat ostrzegawczy.

## <a name="see-also"></a>Zobacz też
- [Obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md)