---
title: 'Jak: Określ środowisko uruchomieniowe programu .NET Framework | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4ab53a6cf265b36ee423a2df176014187860f635
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778677"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Instrukcje: określanie środowiska uruchomieniowego programu .NET Framework

Wraz z wydaniem programu .NET Framework 4 aplikacje mogą składać się z modułów, które zostały utworzone przy użyciu różnych wersji czasu wykonywania programu .NET Framework. Domyślnie Visual Studio Profilowanie Tools profil pierwszego środowiska uruchomieniowego, który jest ładowany przez aplikację. Można określić czas wykonywania profilu podczas uruchamiania aplikacji z profilera i po dołączeniu profilera do już uruchomionej aplikacji.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Aby określić czas wykonywania programu .NET Framework do profilu podczas uruchamiania aplikacji za pomocą profilera

1. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy sesję wydajności, kliknij polecenie **Właściwości**, a następnie kliknij polecenie **Zaawansowane**.

     W polu listy **Docelowa wersja CLR** jest **wyświetlana wersja automatyczna** i wersje środowiska wykonawczego programu .NET Framework zainstalowane na komputerze.

2. Wykonaj jedną z następujących czynności:

    - Kliknij wersję programu CLR, którą chcesz profilować.

    - Kliknij **przycisk Automatycznie,** aby profilu pierwszej wersji, która jest ładowana przez aplikację.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Aby określić czas wykonywania programu .NET Framework do profilu podczas dołączania profilera do aplikacji

1. W menu **Analizuj** wskaż **polecenie Profiler**, a następnie kliknij przycisk **Dołącz/Odłącz**.

2. W oknie dialogowym **Dołączanie profilera do procesu** kliknij proces, który chcesz profilować.

     Pole listy **Docelowa wersja CLR** s **Automatyczna** i wersje środowiska wykonawczego programu .NET Framework zainstalowane na komputerze.

3. Wykonaj jedną z następujących czynności:

    - Kliknij wersję programu CLR, którą chcesz profilować.

    - Kliknij **przycisk Automatycznie,** aby profilu wersji, która jest ładowana, gdy profiler dołącza do aplikacji.
