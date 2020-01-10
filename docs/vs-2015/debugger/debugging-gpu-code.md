---
title: Debugowanie kodu GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5092a2d2a823db6b101ee73d9d5c5dddef5c4526
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75843984"
---
# <a name="debugging-gpu-code"></a>Debugowanie kodu GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można debugować C++ kod, który jest uruchomiony w procesorze GPU. Obsługa debugowania GPU w programie Visual Studio obejmuje wykrywanie wyścigu, uruchamianie procesów i ich dołączanie oraz integrację z oknami debugowania.  
  
## <a name="supported-platforms"></a>Obsługiwane platformy  
 Debugowanie jest obsługiwane w [!INCLUDE[win7](../includes/win7-md.md)], [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]i [!INCLUDE[winserver8](../includes/winserver8-md.md)]. Na potrzeby debugowania na emulatorze oprogramowania jest wymagane [!INCLUDE[win8](../includes/win8-md.md)]lub [!INCLUDE[winserver8](../includes/winserver8-md.md)]. Na potrzeby debugowania sprzętu należy zainstalować sterowniki karty graficznej. Nie wszyscy dostawcy sprzętu implementują wszystkie funkcje debugera. Zapoznaj się z dokumentacją dostawcy, aby uzyskać ograniczenia.  
  
> [!NOTE]
> Niezależni dostawcy sprzętu, którzy chcą obsługiwać debugowanie procesora GPU w programie Visual Studio, muszą utworzyć bibliotekę DLL, która implementuje interfejs VSD3DDebug i jest przeznaczony dla własnych sterowników.  
  
## <a name="configuring-gpu-debugging"></a>Konfigurowanie debugowania procesora GPU  
 Debuger nie może przerwać obu kodów procesora i procesora GPU w tym samym wykonaniu aplikacji. Domyślnie debuger dzieli się na kod procesora CPU. Aby debugować kod procesora GPU, użyj jednego z następujących dwóch kroków:  
  
- Na liście **Typ debugowania** na pasku narzędzi **Standardowy** wybierz pozycję **tylko procesor GPU**.  
  
- W **Eksplorator rozwiązań**, w menu skrótów dla projektu, wybierz **Właściwości**. W oknie dialogowym **strony właściwości** wybierz pozycję **debugowanie**, a następnie na liście **Typ debugera** wybierz pozycję **GPU** .  
  
## <a name="launching-and-attaching-to-applications"></a>Uruchamianie i dołączanie do aplikacji  
 Możesz użyć poleceń debugowania programu Visual Studio, aby uruchomić i zatrzymać debugowanie procesora GPU. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera za](../debugger/navigating-through-code-with-the-debugger.md). Debuger GPU można także dołączyć do uruchomionego procesu, ale tylko wtedy, gdy ten proces wykonuje kod procesora GPU. Aby uzyskać więcej informacji, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Uruchom bieżący kafelek do kursora i uruchom do kursora  
 Podczas debugowania na procesorze GPU dostępne są dwie opcje uruchamiania do lokalizacji kursora. Polecenia dla obu opcji są dostępne w menu skrótów edytora kodu.  
  
1. Polecenie **Uruchom do kursora** uruchamia aplikację do momentu, aż osiągnie lokalizację kursora, a następnie przerwie. Nie oznacza to, że bieżący wątek jest uruchomiony do kursora; nie oznacza to, że pierwszy wątek, który osiągnie punkt kursora wyzwala przerwy. Zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)  
  
2. Polecenie **Uruchom bieżący kafelek do kursora** uruchamia aplikację do momentu, aż wszystkie wątki w bieżącym kafelku osiągną kursora, a następnie przerwie.  
  
## <a name="debugging-windows"></a>Okna debugowania  
 Za pomocą pewnych okien debugowania można testować, flagować i zamrażać wątki GPU. Aby uzyskać więcej informacji, zobacz:  
  
- [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)  
  
- [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)  
  
- [Instrukcje: korzystanie z okna równoległego wyrażenia kontrolnego](../debugger/how-to-use-the-parallel-watch-window.md)  
  
- [Debuguj wątki i procesy](../debugger/debug-threads-and-processes.md) (pasek narzędzi lokalizacji debugowania)  
  
- [Instrukcje: korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## <a name="data-synchronization-exceptions"></a>Wyjątki synchronizacji danych  
 Debuger może zidentyfikować kilka warunków synchronizacji danych podczas wykonywania. Po wykryciu warunku debuger przechodzi do stanu przerwania. Dostępne są dwie opcje —**Przerwij** lub **Kontynuuj**. Za pomocą okna dialogowego **wyjątki** można określić, czy debuger wykrywa te warunki, a także jakie warunki spowodują przerwanie. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md). Możesz również użyć okna dialogowego **Opcje** , aby określić, że debuger powinien ignorować wyjątki, jeśli zapisywana dane nie zmienią wartości danych. Aby uzyskać więcej informacji, zobacz [Ogólne, debugowanie, opcje](../debugger/general-debugging-options-dialog-box.md)— okno dialogowe.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
  
### <a name="specifying-an-accelerator"></a>Określanie akceleratora  
 Punkty przerwania w kodzie GPU są osiągane tylko wtedy, gdy kod jest uruchomiony na akceleratorze [::d irect3d_ref](https://msdn.microsoft.com/library/a514b1a7-3b3f-4011-be6c-f7b0d9a42663) (ref). Jeśli nie określisz akceleratora w kodzie, akcelerator REF jest automatycznie wybierany jako **Typ akceleratora debugowania** we właściwościach projektu. Jeśli kod jawnie wybiera akcelerator, akcelerator REF nie będzie używany podczas debugowania, a punkty przerwania nie będą trafiać, chyba że sprzęt procesora GPU ma obsługę debugowania. Można to naprawić, pisząc swój kod, tak aby używał akceleratora REF podczas debugowania. Aby uzyskać więcej informacji, zobacz właściwości projektu i [Używanie akceleratora i accelerator_view obiektów](https://msdn.microsoft.com/library/18f0dc66-8236-4420-9f46-1a14f2c3fba1) oraz [ustawień projektu C++ dla konfiguracji debugowania](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="conditional-breakpoints"></a>Warunkowe punkty przerwania  
 Warunkowe punkty przerwania w kodzie GPU są obsługiwane, ale nie każde wyrażenie może być oceniane na urządzeniu. Gdy nie można obliczyć wyrażenia na urządzeniu, jest ono oceniane w debugerze. Debuger może działać wolniej niż urządzenie.  
  
### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Błąd: Wystąpił problem z konfiguracją z wybranym typem akceleratora debugowania.  
 Ten błąd występuje w przypadku niespójności między ustawieniami projektu i konfiguracją komputera, na którym odbywa się debugowanie. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Błąd: Sterownik debugowania dla wybranego typu akceleratora debugowania nie jest zainstalowany na maszynie docelowej.  
 Ten błąd występuje w przypadku debugowania na komputerze zdalnym. Debuger nie może ustalić czasu uruchomienia sterowników na komputerze zdalnym. Sterowniki są dostępne od producenta karty graficznej.  
  
### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Błąd: wykrywanie limitu czasu i odzyskiwanie (TDR) musi być wyłączone w lokacji zdalnej.  
 Istnieje możliwość, że C++ obliczenia amp przekroczą domyślny interwał czasu ustawiony przez proces wykrywania i odzyskiwania limitu czasu systemu Windows. W takim przypadku Obliczanie zostanie anulowane, a dane zostaną utracone. Aby uzyskać więcej informacji, zobacz temat [Obsługa C++ TDRs w amp](https://blogs.msdn.com/b/nativeconcurrency/archive/2012/03/07/handling-tdrs-in-c-amp.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: debugowanie aplikacji C++ amp](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Rozpocznij debugowanie procesora GPU w programie Visual Studio](https://blogs.msdn.com/b/nativeconcurrency/archive/2012/03/17/start-gpu-debugging-in-visual-studio-11.aspx)
