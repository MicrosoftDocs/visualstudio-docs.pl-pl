---
title: Debugowanie kodu GPU | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1de8b942b64de56b93b2fece3f46b23413b6981
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60038284"
---
# <a name="debugging-gpu-code"></a>Debugowanie kodu GPU
Można debugować kodu C++, który działa na jednostka przetwarzania grafiki (GPU). Obsługa w programie Visual Studio do debugowania GPU obejmuje wykrywania wyścigu, uruchamianie procesów i dołączanie do, a Integracja debugowania systemu windows.

## <a name="supported-platforms"></a>Obsługiwane platformy
 Debugowanie jest obsługiwane w [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)], i [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)]. Do debugowania na emulatorze oprogramowania [!INCLUDE[win8](../debugger/includes/win8_md.md)], lub [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] jest wymagana. Do debugowania na sprzęcie, należy zainstalować sterowniki dla karty graficznej. Nie wszyscy dostawcy sprzętu zaimplementuj wszystkie funkcje debugera. W dokumentacji dostawcy ograniczenia.

> [!NOTE]
>  Niezależnych dostawców sprzętu, którzy mają być obsługiwane debugowania GPU w programie Visual Studio, należy utworzyć bibliotekę DLL, która implementuje interfejs VSD3DDebug i elementy docelowe swoje własne sterowniki.

## <a name="configuring-gpu-debugging"></a>Konfigurowanie debugowania GPU
 Debuger nie można przerwać w kodzie procesora CPU i procesora GPU kodu w tym samym wykonywanie aplikacji. Domyślnie debuger przerywa na kodzie procesora CPU. Debugowanie kodu GPU, użyj jednej z tych dwóch kroków:

- W **debugowania typu** listy na **standardowa** narzędzi, wybierz **tylko GPU**.

- W **Eksploratora rozwiązań**, w menu skrótów dla projektu, wybierz **właściwości**. W **stron właściwości** okno dialogowe, wybierz opcję **debugowanie**, a następnie wybierz pozycję **tylko GPU** w **typ debugera** listy.

## <a name="launching-and-attaching-to-applications"></a>Uruchamianie i dołączanie do aplikacji
 Za pomocą poleceń debugowania programu Visual Studio uruchamianie i zatrzymywanie debugowania GPU. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera za](../debugger/navigating-through-code-with-the-debugger.md). Można również dołączyć debuger procesora GPU do uruchomionego procesu, ale tylko wtedy, jeśli ten proces wykonuje kodu GPU. Aby uzyskać więcej informacji, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Uruchom bieżący Kafelek do kursora a następnie uruchom do kursora
 Podczas debugowania na procesorze GPU, masz dwie opcje uruchamiania do lokalizacji kursora. Polecenia dla obu opcji są dostępne w menu skrótów w edytorze kodu.

1. **Uruchom do kursora** polecenie uruchamia aplikację, dopóki nie osiągnie lokalizacji kursora, a następnie przerywa. Nie oznacza to, że bieżący wątek działa do kursora; przeciwnie oznacza to, czy pierwszy wątek, który osiągnie punktu kursora wyzwala przerwy. Zobacz [w nawigowaniu po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)

2. **Uruchom bieżący Kafelek do kursora** polecenie uruchamia aplikację, aż wszystkie wątki w bieżącym fragmencie kursora, a następnie podziału.

## <a name="debugging-windows"></a>Debugowanie Windows
 Za pomocą niektórych okien debugowania, można sprawdzić, Flaga i Zablokuj wątki procesora GPU. Aby uzyskać więcej informacji, zobacz:

- [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)

- [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)

- [Instrukcje: Korzystanie z okna równoległego wyrażenia kontrolnego](../debugger/how-to-use-the-parallel-watch-window.md)

- [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md) (pasek narzędzi debugowania lokalizacji)

- [Instrukcje: Korzystanie z okna wątków procesora GPU](../debugger/how-to-use-the-gpu-threads-window.md)

## <a name="data-synchronization-exceptions"></a>Wyjątki synchronizacji danych
 Debuger można określić wiele warunków synchronizacji danych podczas wykonywania. Gdy zostanie wykryty warunek, debuger przejdzie w stan przerwania. Dostępne są dwie opcje —**Przerwij** lub **Kontynuuj**. Za pomocą **wyjątki** okno dialogowe, możesz określić, czy debuger wykryje te warunki, a także jakich warunkach go spowoduje przerwanie dla. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md). Można również użyć **opcje** okno dialogowe, aby określić, czy debuger powinien Ignoruj wyjątki, jeśli dane, które są zapisywane nie zmienia wartość danych. Aby uzyskać więcej informacji, zobacz [ogólne, debugowanie, okno dialogowe Opcje](../debugger/general-debugging-options-dialog-box.md).

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="specifying-an-accelerator"></a>Określanie klawiszy skrótów
 Punkty przerwania w kodzie procesora GPU tylko są osiągane, jeśli kod jest uruchomiony na [Accelerator::direct3d_ref —](/cpp/parallel/amp/reference/accelerator-class#direct3d_ref) akcelerator (REF). Jeśli nie określisz akceleratora w kodzie, akcelerator REF jest automatycznie wybierany jako **typowi akceleratora debugowania** we właściwościach projektu. Jeśli Twój kod jawnie wybiera akcelerator, akcelerator REF nie będą używane podczas debugowania, a punkty przerwania nie zostanie uruchomiona, jeśli sprzęt procesora GPU nie ma obsługi debugowania. Użytkownik może rozwiązać ten problem przez napisanie kodu, tak aby używał akcelerator REF podczas debugowania. Aby uzyskać więcej informacji, zobacz właściwości projektu i [używanie akceleratora i obiektów accelerator_view](/cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) i [ustawienia projektu dla C++ konfiguracji debugowania](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="conditional-breakpoints"></a>Warunkowe punkty przerwania
 Warunkowe punkty przerwania w kodzie GPU są obsługiwane, ale nie każde wyrażenie może przyjąć na urządzeniu. Gdy na urządzeniu nie można obliczyć wyrażenia, sprawdzana jest zgodność to debugera. Debuger będzie prawdopodobnie działać wolniej niż urządzenia.

### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Błąd: Istnieje problem konfiguracji wybranego typu akceleratora debugowania.
 Ten błąd występuje, gdy występuje niespójność między ustawień projektu i konfiguracji komputera, na którym wykonujesz debugowanie na. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Błąd: Na komputerze docelowym nie zainstalowano sterownika debugowania odpowiadającego wybranemu typowi akceleratora debugowania.
 Ten błąd występuje, Jeśli debugujesz na komputerze zdalnym. Debuger nie może określić do czasu wykonywania, czy sterowniki są zainstalowane na komputerze zdalnym. Sterowniki są dostępne od producenta karty graficznej.

### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Błąd: I wykrywania limitu czasu odzyskiwania (TDR) musi być wyłączone w lokacji zdalnej.
 Istnieje możliwość dla obliczeń C++ AMP może przekroczyć domyślny interwał czasu jest ustawiana przez proces odzyskiwania (TDR) i wykrywania limitu czasu Windows. Jeśli tak się stanie, obliczenie zostanie anulowane, a dane zostaną utracone. Aby uzyskać więcej informacji, zobacz [obsługi TDR w bibliotece C++ AMP](http://go.microsoft.com/fwlink/p/?LinkId=249154).

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)
- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Rozpocznij debugowanie GPU w programie Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=255381)