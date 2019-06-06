---
title: 'Instrukcje: Określanie środowiska wykonawczego .NET Framework | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f0179be3aa5ca55eef0854cc68a7e1287ac284f1
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746425"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Instrukcje: Określanie środowiska uruchomieniowego programu .NET Framework

Wraz z wydaniem programu .NET Framework 4 aplikacje mogą się składać z modułów, które zostały utworzone przy użyciu różnych wersji środowiska wykonawczego .NET Framework. Domyślnie Visual Studio Profiling Tools profilowanie pierwszego środowiska uruchomieniowego, który jest ładowany przez aplikację. Można określić czasu wykonywania, aby przeprowadzić profilowanie, podczas uruchamiania aplikacji przy użyciu profilera i dołączenia programu profilującego do aplikacji już uruchomionego.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Aby określić środowiska wykonawczego .NET Framework do profilowania, podczas uruchamiania aplikacji przy użyciu profilera

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, kliknij przycisk **właściwości**, a następnie kliknij przycisk **zaawansowane**.

     **Docelowa wersja środowiska CLR** liście wyświetlane są **automatyczne** i wersje środowiska uruchomieniowego .NET Framework, które są zainstalowane na komputerze.

2. Wykonaj jedną z następujących czynności:

    - Kliknij wersję środowiska CLR, które powinny być profilowane.

    - Kliknij przycisk **automatyczne** profilowanie pierwszej wersji, który jest ładowany przez aplikację.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Aby określić środowiska wykonawczego .NET Framework do profilowania, podczas dołączania profilera do aplikacji

1. Na **analizy** menu wskaż **Profiler**, następnie kliknij przycisk **Attach/Detach**.

2. Na **dołączyć Profiler do procesu** okna dialogowego kliknij proces, który chcesz profilować.

     **Docelowa wersja środowiska CLR** pole z listy s **automatyczne** i wersje środowiska uruchomieniowego .NET Framework, które są zainstalowane na komputerze.

3. Wykonaj jedną z następujących czynności:

    - Kliknij wersję środowiska CLR, które powinny być profilowane.

    - Kliknij przycisk **automatyczne** do profilowania, wersji, który jest ładowany, gdy program profilujący jest dołączony do aplikacji.