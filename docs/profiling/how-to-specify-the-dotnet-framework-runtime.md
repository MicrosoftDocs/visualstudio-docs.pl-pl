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
ms.openlocfilehash: d9c62e430d19bbd2c03afbb4db76fca56563cb3c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632670"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Instrukcje: Określanie środowiska uruchomieniowego programu .NET Framework

Wraz z wydaniem [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], aplikacje mogą się składać z modułów, które zostały utworzone przy użyciu różnych wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] środowiska wykonawczego. Domyślnie Visual Studio Profiling Tools profilowanie pierwszego środowiska uruchomieniowego, który jest ładowany przez aplikację. Można określić czasu wykonywania, aby przeprowadzić profilowanie, podczas uruchamiania aplikacji przy użyciu profilera i dołączenia programu profilującego do aplikacji już uruchomionego.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Aby określić środowiska wykonawczego .NET Framework do profilowania, podczas uruchamiania aplikacji przy użyciu profilera

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, kliknij przycisk **właściwości**, a następnie kliknij przycisk **zaawansowane**.

     **Docelowa wersja środowiska CLR** liście wyświetlane są **automatyczne** oraz wersje [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] środowiska uruchomieniowego, które są zainstalowane na komputerze.

2. Wykonaj jedną z następujących czynności:

    - Kliknij wersję środowiska CLR, które powinny być profilowane.

    - Kliknij przycisk **automatyczne** profilowanie pierwszej wersji, który jest ładowany przez aplikację.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Aby określić środowiska wykonawczego .NET Framework do profilowania, podczas dołączania profilera do aplikacji

1. Na **analizy** menu wskaż **Profiler**, następnie kliknij przycisk **Attach/Detach**.

2. Na **dołączyć Profiler do procesu** okna dialogowego kliknij proces, który chcesz profilować.

     **Docelowa wersja środowiska CLR** pole z listy s **automatyczne** oraz wersje [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] środowiska uruchomieniowego, które są zainstalowane na komputerze.

3. Wykonaj jedną z następujących czynności:

    - Kliknij wersję środowiska CLR, które powinny być profilowane.

    - Kliknij przycisk **automatyczne** do profilowania, wersji, który jest ładowany, gdy program profilujący jest dołączony do aplikacji.