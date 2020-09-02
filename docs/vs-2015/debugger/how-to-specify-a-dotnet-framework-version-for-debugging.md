---
title: 'Instrukcje: Określanie wersji .NET Framework na potrzeby debugowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c785c419ead31ad90e2b20ae7f48af778598bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176559"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Porady: określanie wersji programu .NET Framework do debugowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]Debuger obsługuje debugowanie starszych wersji firmy Microsoft, a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] także bieżącą wersję. Po uruchomieniu aplikacji z programu Visual Studio debuger zawsze może zidentyfikować poprawną wersję programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dla debugowanej aplikacji. Jeśli aplikacja jest już uruchomiona i używasz **dołączania do**programu, debuger może nie zawsze mieć możliwości zidentyfikowania starszej wersji programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . W takim przypadku zostanie wyświetlony komunikat o błędzie z informacją,  
  
 Debuger wprowadził nieprawidłowe założenie dotyczące wersji, która ma być [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] używana przez aplikację.  
  
 W tych rzadkich przypadkach można ustawić klucz rejestru, aby wskazać debugerowi, którego wersja ma używać.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Aby określić wersję .NET Framework do debugowania  
  
1. W katalogu Windows\Microsoft.NET\Framework Znajdź wersje .NET Framework zainstalowanych na maszynie. Numery wersji wyglądają następująco:  
  
     `V1.1.4322`  
  
     Zidentyfikuj poprawny numer wersji i zanotuj go.  
  
2. Uruchom **Edytor rejestru** (regedit).  
  
3. W **Edytorze rejestru**otwórz folder HKEY_LOCAL_MACHINE.  
  
4. Przejdź do: HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine \\ {449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Jeśli klucz nie istnieje, kliknij prawym przyciskiem myszy pozycję HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, a następnie kliknij pozycję **nowy klucz**. Nadaj nazwę nowemu kluczowi `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` .  
  
5. Po przejściu do programu {449EC4CC-30D2-4032-9256-EE18EB41B62B} zajrzyj do kolumny **name (nazwa** ) i Znajdź klucz CLRVersionForDebugging.  
  
    1. Jeśli klucz nie istnieje, kliknij prawym przyciskiem myszy pozycję {449EC4CC-30D2-4032-9256-EE18EB41B62B}, a następnie kliknij pozycję **Nowa wartość ciągu**. Następnie kliknij prawym przyciskiem myszy nową wartość ciągu, kliknij polecenie **Zmień nazwę**i wpisz `CLRVersionForDebugging` .  
  
6. Kliknij dwukrotnie pozycję **CLRVersionForDebugging**.  
  
7. W polu **Edytuj ciąg** wpisz numer wersji .NET Framework w polu **wartość** . Na przykład: V 1.1.4322  
  
8. Kliknij przycisk **OK**.  
  
9. Zamknij **Edytor rejestru**.  
  
     Jeśli po rozpoczęciu debugowania nadal pojawia się komunikat o błędzie, sprawdź, czy w rejestrze wprowadzono numer wersji. Sprawdź również, czy używasz wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] obsługiwanej przez program Visual Studio. Debuger jest zgodny z bieżącą wersją .NET Framework i poprzednimi wersjami, ale może nie być zgodny z przyszłymi wersjami.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
