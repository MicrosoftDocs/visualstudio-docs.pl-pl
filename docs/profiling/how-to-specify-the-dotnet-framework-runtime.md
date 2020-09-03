---
title: Jak określić środowisko uruchomieniowe .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 2eddbe3602386e6a8f5c7e07e796b8c3b047603c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331378"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Instrukcje: określanie środowiska uruchomieniowego programu .NET Framework

W wersji .NET Framework 4 aplikacje mogą składać się z modułów, które zostały skompilowane przy użyciu różnych wersji .NET Framework czasie wykonywania. Domyślnie program Visual Studio narzędzia profilowania profiluje pierwsze środowisko uruchomieniowe, które jest ładowane przez aplikację. Możesz określić czas wykonywania do profilowania, gdy uruchamiasz aplikację za pomocą profilera i po dołączeniu profilera do już uruchomionej aplikacji.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Aby określić .NET Framework czas wykonywania do profilowania podczas uruchamiania aplikacji za pomocą profilera

1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, kliknij polecenie **Właściwości**, a następnie kliknij przycisk **Zaawansowane**.

     Pole listy **docelowa wersja środowiska CLR** zawiera **Automatyczne** i wersje środowiska uruchomieniowego .NET Framework, które są zainstalowane na komputerze.

2. Wykonaj jedną z następujących czynności:

    - Kliknij wersję środowiska CLR, które chcesz profilować.

    - Kliknij pozycję **Automatyczne** , aby profilować pierwszą wersję, która jest ładowana przez aplikację.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Aby określić .NET Framework czasie wykonywania do profilowania podczas dołączania profilera do aplikacji

1. W menu **Analizuj** wskaż polecenie **Profiler**, a następnie kliknij pozycję **Dołącz/Odłącz**.

2. W oknie dialogowym **Dołącz profiler do procesu** kliknij proces, który chcesz profilować.

     Pole listy **docelowa wersja środowiska CLR** **s i** wersje środowiska uruchomieniowego .NET Framework zainstalowane na komputerze.

3. Wykonaj jedną z następujących czynności:

    - Kliknij wersję środowiska CLR, które chcesz profilować.

    - Kliknij pozycję **Automatyczne** , aby profilować wersję załadowana podczas dołączania profilera do aplikacji.
