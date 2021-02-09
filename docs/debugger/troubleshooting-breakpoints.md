---
title: Rozwiązywanie problemów z punktami przerwania w debugerze | Microsoft Docs
description: Jeśli punkt przerwania jest wyłączony lub nie można go ustawić, jest wyświetlany jako koło puste. W tym miejscu znajdziesz informacje dotyczące problemów, które mogą wystąpić podczas ustawiania punktów przerwania.
ms.custom: SEO-VS-2020, seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bb7d2d15e9cb04b541fba3d68607fb250054b707
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870431"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Rozwiązywanie problemów z punktami przerwania w debugerze programu Visual Studio

## <a name="breakpoint-warnings"></a>Ostrzeżenia punktów przerwania

Podczas debugowania punkt przerwania ma dwa możliwe stany wizualizacji: pełny czerwony okrąg i pusty (biały kolor) okrąg. Jeśli debuger może pomyślnie ustawić punkt przerwania w procesie docelowym, pozostanie Solid czerwony okrąg. Jeśli punkt przerwania jest kółkiem pustym, punkt przerwania jest wyłączony lub wystąpiło ostrzeżenie podczas próby ustawienia punktu przerwania. Aby określić różnicę, umieść kursor nad punktem przerwania i sprawdź, czy występuje ostrzeżenie.

W poniższych dwóch sekcjach opisano widoczne ostrzeżenia i sposoby ich naprawiania.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Nie załadowano żadnych symboli dla tego dokumentu"

Przejdź do okna **moduły** (**debugowanie**  >  modułów **systemu Windows**  >  ) i sprawdź, czy moduł jest załadowany.
* Jeśli moduł jest załadowany, Sprawdź kolumnę **stan symbolu** , aby sprawdzić, czy symbole zostały załadowane.
  * Jeśli symbole nie są załadowane, sprawdź stan symbolu, aby zdiagnozować problem. Z menu kontekstowego modułu w oknie **moduły** kliknij pozycję **Informacje o załadowaniu symboli...** , aby zobaczyć, gdzie debuger ma próbować i załadować symbole. Aby uzyskać więcej informacji na temat ładowania symboli, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Jeśli symbole są załadowane, PDB nie zawiera informacji o plikach źródłowych. Oto kilka możliwych przyczyn:
    * Jeśli pliki źródłowe zostały ostatnio dodane, potwierdź, że jest ładowana aktualna wersja modułu.
    * Można utworzyć usunięte plików PDB przy użyciu opcji konsolidatora **/PDBSTRIPPED** . Usunięte plików PDB nie zawierają informacji o pliku źródłowym. Upewnij się, że pracujesz z pełnym PDB, a nie z usuniętym PDB.
    * Plik PDB jest częściowo uszkodzony. Usuń plik i Wykonaj czystą kompilację modułu, aby spróbować rozwiązać ten problem.

* Jeśli moduł nie jest załadowany, sprawdź poniższe informacje, aby znaleźć przyczynę:
  * Upewnij się, że debugujesz właściwy proces.
  * Sprawdź, czy debugujesz właściwy rodzaj kodu. Możesz dowiedzieć się, jakiego typu kodu debuger jest skonfigurowany do debugowania w oknie **procesy** (**debugowanie**  >  **procesów systemu Windows**  >  ). Na przykład, jeśli próbujesz debugować kod w języku C#, upewnij się, że debuger jest skonfigurowany dla odpowiedniego typu i wersji platformy .NET (na przykład zarządzane (v4 \* ) i zarządzane (v2 \* /v3) i \* zarządzane (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… bieżący kod źródłowy różni się od wersji wbudowanej w... "

Jeśli plik źródłowy został zmieniony i źródło nie pasuje już do kodu, który jest debugowany, debuger nie ustawi domyślnie punktów przerwania w kodzie. Zazwyczaj ten problem występuje, gdy plik źródłowy zostanie zmieniony, ale kod źródłowy nie został odbudowany. Aby rozwiązać ten problem, ponownie skompiluj projekt. Jeśli system kompilacji uzna, że projekt jest już aktualny, nawet jeśli nie jest, można wymusić ponowne kompilowanie systemu projektu przez zapisanie pliku źródłowego lub oczyszczenie danych wyjściowych kompilacji projektu przed kompilacją.

W rzadkich scenariuszach może być konieczne debugowanie bez konieczności używania kodu źródłowego. Debugowanie bez zgodnego kodu źródłowego może prowadzić do mylącego debugowania, dlatego należy się upewnić, że jest to konieczne.

Aby wyłączyć te kontrole bezpieczeństwa, wykonaj jedną z następujących czynności:
* Aby zmodyfikować pojedynczy punkt przerwania, umieść kursor nad ikoną punktu przerwania w edytorze i kliknij ikonę Ustawienia (koła zębate). Okno wglądu jest dodawane do edytora. W górnej części okna wglądu istnieje hiperłącze wskazujące lokalizację punktu przerwania. Kliknij hiperlink, aby zezwolić na modyfikację lokalizacji punktu przerwania i sprawdź, czy **kod źródłowy różni się od oryginału**.
* Aby zmodyfikować to ustawienie dla wszystkich punktów przerwania, przejdź do opcji **debugowania**  >  **i ustawienia**. Na stronie **debugowanie/ogólne** wyczyść pole wyboru **Wymagaj plików źródłowych, które dokładnie pasują do oryginalnej wersji** . Upewnij się, że ta opcja jest ponownie włączona po zakończeniu debugowania.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Punkt przerwania został pomyślnie ustawiony (bez ostrzeżenia), ale nie został trafiony

Ta sekcja zawiera informacje dotyczące rozwiązywania problemów, gdy w debugerze nie są wyświetlane żadne ostrzeżenia — punkt przerwania jest całkowicie czerwonym kółkiem podczas aktywnego debugowania, ale punkt przerwania nie jest aktywny.

Oto kilka rzeczy do sprawdzenia:
1. Jeśli kod działa w więcej niż jednym procesie lub więcej niż jednym komputerze, należy się upewnić, że debugowano właściwy proces lub komputer.
2. Upewnij się, że Twój kod jest uruchomiony. Aby sprawdzić, czy kod jest uruchomiony, Dodaj wywołanie do `System.Diagnostics.Debugger.Break` (C#/VB) lub `__debugbreak` (C++) do wiersza kodu, w którym próbujesz ustawić punkt przerwania, a następnie ponownie skompiluj projekt.
3. W przypadku debugowania zoptymalizowanego kodu upewnij się, że funkcja, w której ustawiono punkt przerwania, nie jest wbudowana w inną funkcję. `Debugger.Break`Test opisany w poprzednim sprawdzaniu może obsłużyć również test tego problemu.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Po usunięciu punktu przerwania nadal go klikam, gdy Rozpocznij debugowanie ponownie

Jeśli podczas debugowania został usunięty punkt przerwania, można ponownie uruchomić punkt przerwania przy następnym rozpoczęciu debugowania. Aby przerwać ten punkt przerwania, upewnij się, że wszystkie wystąpienia punktu przerwania są usuwane z okna **punkty przerwania** .
