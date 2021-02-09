---
title: Zalecane ustawienia właściwości debugera dla języków C#, VB | Microsoft Docs
description: Sprawdź ustawienia właściwości kompilacja i kompilacja, które powinny być takie same dla wszystkich zarządzanych debugowania. Inne ustawienia mogą się różnić w zależności od typu projektu.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: b3061823a97faa53680bb358475a583493be5b93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893103"
---
# <a name="managed-debugging-recommended-property-settings"></a>Zarządzanie debugowaniem: zalecane ustawienia właściwości
Niektóre właściwości powinny być ustawiane w taki sam sposób dla wszystkich zarządzanych scenariuszy debugowania.

 W poniższych tabelach są wyświetlane zalecane ustawienia właściwości.

 Ustawienia niewymienione w tym miejscu mogą się różnić między różnymi typami projektów zarządzanych. Na przykład **Akcja uruchamiania** zostanie ustawiona inaczej w projekcie Windows Forms niż w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projekcie.

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Właściwości konfiguracji na karcie kompilacja (C#) lub kompilacja (Visual Basic)

|**Nazwa właściwości**|**Ustawienie**|
|-----------------------|-----------------|
|**Zdefiniuj stałą DEBUG**|C# i F #: Ustaw pole wyboru zaznaczone. Dzięki temu aplikacja może używać klasy Debug.|
|**Zdefiniuj stałą TRACE**|C# i F #: Ustaw pole wyboru zaznaczone. Dzięki temu aplikacja może używać klasy śledzenia.|
|**Optymalizuj kod**|C#, F # i Visual Basic: Ustaw wartość false. Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio na kod źródłowy. Jeśli okaże się, że program ma usterkę, która pojawia się tylko w zoptymalizowanym kodzie, można włączyć to ustawienie, ale pamiętaj, że kod wyświetlany w oknie **demontażu** jest generowany na podstawie zoptymalizowanego źródła, które może nie odpowiadać temu, co widzisz w edytorze kodu. Aby debugować zoptymalizowany kod, należy wyłączyć Tylko mój kod. (Zobacz [ograniczanie do tylko mój kod](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Aby uzyskać więcej informacji, zobacz [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md) lub [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|
|**Ścieżka wyjściowa**|Ustaw wartość bin\Debug \\ .|
|**Zaawansowane opcje kompilacji**|Tylko Visual Basic. Kliknij przycisk **Zaawansowane** , aby ustawić zaawansowane właściwości, które są opisane w poniższej tabeli.|

### <a name="advanced-compiler-settings-dialog-box"></a>Zaawansowane ustawienia kompilatora — Okno dialogowe

|**Nazwa właściwości**|**Ustawienie**|
|-----------------------|-----------------|
|**Włącz optymalizacje**|Ustaw wartość false dla powodów określonych w opcji **Optymalizuj kod** w powyższej tabeli.|
|**Generuj informacje o debugowaniu**|Zaznacz to pole wyboru, aby spowodować, że flaga/DEBUG ma być ustawiana podczas kompilacji, co spowoduje wygenerowanie informacji niezbędnych do ułatwienia debugowania.|
|**Zdefiniuj stałą DEBUG**|Zaznacz to pole wyboru, aby zdefiniować `DEBUG` stałą, która umożliwia aplikacji korzystanie z <xref:System.Diagnostics.Debug> klasy.|
|**Zdefiniuj stałą TRACE**|Zaznacz to pole wyboru, aby zdefiniować `TRACE` stałą, która umożliwia aplikacji korzystanie z <xref:System.Diagnostics.Trace> klasy.|

## <a name="see-also"></a>Zobacz też
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)