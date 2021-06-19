---
title: Zalecane ustawienia właściwości debugera dla języka C#, VB | Microsoft Docs
description: Zobacz ustawienia właściwości kompilacji i kompilacji, które powinny być takie same dla całego zarządzanego debugowania. Inne ustawienia mogą się różnić w zależności od typu projektu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c2262194dbb6a8f4b0a47b4fcfc7f9f696c60167
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390401"
---
# <a name="managed-debugging-recommended-property-settings"></a>Zarządzanie debugowaniem: zalecane ustawienia właściwości
Niektóre właściwości powinny być ustawione w taki sam sposób dla wszystkich scenariuszy debugowania zarządzanego.

 W poniższych tabelach są wyświetlane zalecane ustawienia właściwości.

 Ustawienia, których nie wymieniono w tym miejscu, mogą się różnić w zależności od typu projektu zarządzanego. Na przykład akcja **uruchamiania** zostanie ustawiona inaczej w Windows Forms niż w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projekcie.

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Właściwości konfiguracji na karcie Kompilacja (C#) lub Kompilowanie (Visual Basic)

|**Nazwa właściwości**|**Ustawienie**|
|-----------------------|-----------------|
|**Definiowanie stałej DEBUG**|C# i F#: zaznacz pole wyboru. Dzięki temu aplikacja może używać klasy Debug.|
|**Definiowanie stałej TRACE**|C# i F#: zaznacz pole wyboru. Dzięki temu aplikacja może używać klasy Trace.|
|**Optymalizowanie kodu**|C#, F# i Visual Basic: ustaw wartość false. Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio kodowi źródłowemu. Jeśli okaże się, że program ma usterkę, która pojawia się tylko w zoptymalizowanym  kodzie, możesz włączyć to ustawienie, ale pamiętaj, że kod wyświetlany w oknie Dekompełowanie jest generowany ze zoptymalizowanego źródła, które może nie odpowiadać temu, co widzisz w Edytorze kodu. Aby debugować zoptymalizowany kod, należy wyłączyć Tylko mój kod. (Zobacz [Ograniczanie przechodzenia krokowego do Tylko mój kod](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Aby uzyskać więcej informacji, zobacz Project Settings for C# Debug Configurations (Ustawienia projektu dla konfiguracji debugowania w języku [C#)](../debugger/project-settings-for-csharp-debug-configurations.md) lub Project Settings for a Visual Basic Debug Configuration (Konfiguracja debugowania w języku [C#).](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)|
|**Ścieżka wyjściowa**|Ustaw wartość bin\Debug \\ .|
|**Zaawansowane opcje kompilacji**|Visual Basic tylko. Kliknij **pozycję** Zaawansowane, aby ustawić zaawansowane właściwości opisane w poniższej tabeli.|

### <a name="advanced-compiler-settings-dialog-box"></a>Zaawansowane ustawienia kompilatora — Okno dialogowe

|**Nazwa właściwości**|**Ustawienie**|
|-----------------------|-----------------|
|**Włączanie optymalizacji**|Ustaw wartość false z przyczyn określonych w opcji **Optymalizuj** kod w powyższej tabeli.|
|**Generowanie informacji debugowania**|Zaznacz to pole wyboru, aby spowodować ustawienie flagi /DEBUG podczas kompilowania, co spowoduje wygenerowanie informacji potrzebnych do ułatwienia debugowania.|
|**Definiowanie stałej DEBUG**|Zaznacz to pole wyboru, aby zdefiniować `DEBUG` stałą, która umożliwia aplikacji korzystanie z <xref:System.Diagnostics.Debug> klasy .|
|**Definiowanie stałej TRACE**|Zaznacz to pole wyboru, aby zdefiniować `TRACE` stałą, która umożliwia aplikacji korzystanie z <xref:System.Diagnostics.Trace> klasy .|

## <a name="see-also"></a>Zobacz też
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)