---
title: Wyłącz debuger just in Time | Microsoft Docs
description: W przypadku wystąpienia błędu w aplikacji może być otwarte okno dialogowe debuger just in Time. Dowiedz się, co możesz zrobić, gdy tak się stanie, i sposoby ich zapobiegania.
ms.custom: SEO-VS-2020
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 670809ea2c9ef04107dbec5634f40831b68b94c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931503"
---
# <a name="disable-the-just-in-time-debugger"></a>Wyłączanie debugera just in time

Okno dialogowe debuger just in time może zostać otwarte w przypadku wystąpienia błędu w działającej aplikacji i uniemożliwić kontynuowanie działania aplikacji.

Debuger just in Time umożliwia uruchamianie programu Visual Studio w celu debugowania błędu. Aby wyświetlić szczegółowe informacje o błędzie lub spróbować go debugować, musisz mieć zainstalowany program Visual Studio lub inny wybrany debuger.

Jeśli jesteś już użytkownikiem programu Visual Studio i chcesz spróbować debugować błąd, zobacz [debugowanie przy użyciu debugera just in Time](../debugger/debug-using-the-just-in-time-debugger.md). Jeśli nie możesz naprawić błędu lub chcesz zachować debuger just in Time, możesz [wyłączyć debugowanie just in Time z programu Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling).

Jeśli program Visual Studio został zainstalowany, ale nie jest już potrzebny, może być konieczne [wyłączenie debugowania just in Time w rejestrze systemu Windows](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry).

Jeśli nie masz zainstalowanego programu Visual Studio, możesz zapobiec debugowaniu just in Time poprzez wyłączenie debugowania skryptów lub debugowania po stronie serwera.

- Jeśli próbujesz uruchomić aplikację sieci Web, wyłącz debugowanie skryptów:

  W oknie   >  **Opcje sieciowe i internetowe** w panelu sterowania systemu Windows  >  wybierz opcję **Wyłącz debugowanie skryptów (Internet Explorer)** i **Wyłącz debugowanie skryptów (inne)**. Dokładne kroki i ustawienia zależą od używanej wersji systemu Windows i przeglądarki.

  ![Opcje internetowe w trybie JIT](../debugger/media/jitinternetoptions.png "Opcje internetowe w trybie JIT")

- Jeśli przechowujesz aplikację sieci Web ASP.NET w usługach IIS, wyłącz debugowanie po stronie serwera:

  1. W obszarze **Widok funkcji** Menedżera usług IIS w **sekcji ASP.NET** kliknij dwukrotnie pozycję **kompilacja platformy .NET** lub zaznacz ją, a następnie wybierz pozycję **Otwórz funkcję** w okienku **Akcje** .
  1. W obszarze  >  **debugowanie** zachowania wybierz opcję **Fałsz**. Kroki różnią się w przypadku starszych wersji usług IIS.

Po wyłączeniu debugowania just-in-Time aplikacja może być w stanie obsłużyć błąd i działać normalnie.

Jeśli aplikacja nadal ma nieobsługiwany błąd, może zostać wyświetlony komunikat o błędzie lub aplikacja może ulec awarii lub przestać odpowiadać. Aplikacja nie będzie działać normalnie do czasu naprawienia błędu. Możesz spróbować skontaktować się z właścicielem aplikacji i poproś o jej rozwiązanie.
