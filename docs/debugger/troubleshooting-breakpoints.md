---
title: Rozwiązywanie problemów z punktami przerwania w debugerze | Microsoft Docs
description: Jeśli punkt przerwania jest wyłączony lub nie można go ustawić, jest wyświetlany jako pusty okrąg. W tym miejscu można znaleźć informacje o problemach, które mogą wystąpić podczas ustawiania punktów przerwania.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0801a687529b5e0f8cdf34030460f0b5fe45bc91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386387"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Rozwiązywanie problemów z punktami przerwania w Visual Studio debugerze

## <a name="breakpoint-warnings"></a>Ostrzeżenia punktu przerwania

Podczas debugowania punkt przerwania ma dwa możliwe stany wizualizacji: ciągłe czerwone kółko i pusty (biały) okrąg. Jeśli debuger może pomyślnie ustawić punkt przerwania w procesie docelowym, pozostanie stałym czerwonym okręgiem. Jeśli punkt przerwania jest pustym okręgiem, punkt przerwania jest wyłączony lub wystąpiło ostrzeżenie podczas próby ustawienia punktu przerwania. Aby ustalić różnicę, umieść kursor nad punktem przerwania i sprawdź, czy jest wyświetlane ostrzeżenie.

W poniższych dwóch sekcjach opisano ważne ostrzeżenia i sposoby ich naprawiania.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Dla tego dokumentu nie załadowano żadnych symboli"

Przejdź do **okna Moduły** (Debugowanie modułów systemu  >  **Windows)** i  >  sprawdź, czy moduł jest załadowany.
* Jeśli moduł jest załadowany, sprawdź **kolumnę Stan symboli,** aby sprawdzić, czy symbole zostały załadowane.
  * Jeśli symbole nie są ładowane, sprawdź stan symbolu, aby zdiagnozować problem. W menu kontekstowym modułu  w oknie Moduły kliknij pozycję **Informacje** o ładowaniu symboli, aby zobaczyć, gdzie debuger próbował załadować symbole. Aby uzyskać więcej informacji na temat ładowania symboli, zobacz [Określanie symboli (pdb) i Plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Jeśli symbole są ładowane, plik PDB nie zawiera informacji o plikach źródłowych. Oto kilka możliwych przyczyn:
    * Jeśli pliki źródłowe zostały ostatnio dodane, upewnij się, że jest ładowana najnowsza wersja modułu.
    * Możliwe jest utworzenie rozłożonych plików PDB przy użyciu **opcji łączenia /PDBSTRIPPED.** Rozłożone pliki PDB nie zawierają informacji o pliku źródłowym. Upewnij się, że pracujesz z pełnym plikiem PDB, a nie z rozłożonym plikiem PDB.
    * Plik PDB jest częściowo uszkodzony. Usuń plik i wykonaj czystą kompilację modułu, aby spróbować rozwiązać problem.

* Jeśli moduł nie jest załadowany, sprawdź następujące informacje, aby znaleźć przyczynę:
  * Upewnij się, że debugujesz właściwy proces.
  * Sprawdź, czy debugujesz właściwy rodzaj kodu. Typ kodu, który debuger jest skonfigurowany do debugowania, można znaleźć w oknie **Procesy** **(Debugowanie**  >  **procesów systemu**  >  **Windows).** Jeśli na przykład próbujesz debugować kod C#, upewnij się, że debuger jest skonfigurowany dla odpowiedniego typu i wersji programu .NET (na przykład Zarządzane (wersja 4) i Zarządzane (wersja 2 /v3) w porównaniu z zarządzanym \* \* \* (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… bieżący kod źródłowy różni się od wersji wbudowanej w..."

Jeśli plik źródłowy uległ zmianie i źródło nie jest już takie, jak kod, który debugujesz, debuger domyślnie nie ustawi punktów przerwania w kodzie. Zwykle ten problem występuje, gdy plik źródłowy zostanie zmieniony, ale kod źródłowy nie został ponownie skonfektowana. Aby rozwiązać ten problem, ponownie skompilować projekt. Jeśli system kompilacji uważa, że projekt jest już aktualny, mimo że nie, można wymusić ponowne skompilowanie systemu projektu przez ponowne zapisanie pliku źródłowego lub wyczyszczenie danych wyjściowych kompilacji projektu przed kompilacją.

W rzadkich scenariuszach można debugować bez konieczności dopasowywania kodu źródłowego. Debugowanie bez dopasowywania kodu źródłowego może prowadzić do mylącego debugowania, dlatego upewnij się, że chcesz kontynuować.

Aby wyłączyć te kontrole bezpieczeństwa, wykonaj jedną z następujących czynności:
* Aby zmodyfikować pojedynczy punkt przerwania, umieść kursor nad ikoną punktu przerwania w edytorze i kliknij ikonę ustawień (koła zębatego). Do edytora zostanie dodane okno podglądu. W górnej części okna podglądu znajduje się hiperlink, który wskazuje lokalizację punktu przerwania. Kliknij hiperlink, aby zezwolić na modyfikację lokalizacji punktu przerwania i zaznacz pole wyboru Zezwalaj na to, aby **kod źródłowy różnił się od oryginalnego .**
* Aby zmodyfikować to ustawienie dla wszystkich punktów przerwania, przejdź do **opcji**  >  **debugowania i ustawień**. Na stronie **Debugowanie/Ogólne** wyczyść opcję **Wymagaj plików źródłowych, które dokładnie pasują do oryginalnej** wersji. Pamiętaj, aby ponownie wdają się w tę opcję po zakończeniu debugowania.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Punkt przerwania został pomyślnie ustawiony (bez ostrzeżenia), ale nie został trafiony

Ta sekcja zawiera informacje dotyczące rozwiązywania problemów, gdy debuger nie wyświetla żadnych ostrzeżeń — punkt przerwania jest stałym czerwonym okręgiem podczas aktywnego debugowania, ale punkt przerwania nie jest trafiony.

Oto kilka rzeczy do sprawdzenia:
1. Jeśli kod działa w więcej niż jednym procesie lub na więcej niż jednym komputerze, upewnij się, że debugujesz właściwy proces lub komputer.
2. Upewnij się, że kod jest uruchomiony. Aby sprawdzić, czy kod jest uruchomiony, dodaj wywołanie metody `System.Diagnostics.Debugger.Break` (C#/VB) lub (C++) do wiersza kodu, w którym próbujesz ustawić punkt przerwania, a następnie ponownie skompilować `__debugbreak` projekt.
3. W przypadku debugowania zoptymalizowanego kodu upewnij się, że funkcja, w której ustawiono punkt przerwania, nie jest wdawana do innej funkcji. Test opisany w poprzednim teście może również zadziałać w `Debugger.Break` celu przetestowania tego problemu.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Usunę punkt przerwania, ale nadal go trafiam, gdy ponownie rozpoczną się debugowanie

Jeśli usunięto punkt przerwania podczas debugowania, możesz ponownie trafić punkt przerwania przy następnym rozpoczęciu debugowania. Aby zatrzymać trafianie tego punktu przerwania, upewnij się, że wszystkie wystąpienia punktu przerwania zostały usunięte z **okna Punkty przerwania.**
