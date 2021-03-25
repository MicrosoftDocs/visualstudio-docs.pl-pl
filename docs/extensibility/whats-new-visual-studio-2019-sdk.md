---
title: Co nowego w zestawie SDK programu Visual Studio 2019 | Microsoft Docs
description: Zestaw SDK programu Visual Studio zawiera nowe i zaktualizowane funkcje programu Visual Studio 2019, w tym usprawnienia rejestracji edytora.
ms.custom: SEO-VS-2020
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2d8e08136eb142e5e72c08e23860bf94f01dc87c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061904"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Co nowego w zestawie SDK programu Visual Studio 2019

Zestaw Visual Studio SDK zawiera następujące nowe i zaktualizowane funkcje programu Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Ostrzeżenie o synchronicznie załadowanych rozszerzeń

Użytkownicy będą teraz widzieć ostrzeżenie, jeśli którekolwiek z ich zainstalowanych rozszerzeń są synchronicznie ładowane automatycznie przy uruchamianiu. Możesz dowiedzieć się więcej o ostrzeżeniu na [synchronicznie załadowanych rozszerzeniach](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Pojedynczy, ujednolicony zestaw Visual Studio SDK

Teraz można pobrać wszystkie zasoby zestawu SDK programu Visual Studio za pomocą jednego pakietu NuGet [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Usprawnienia rejestracji edytora

Od momentu jego utworzenia program Visual Studio obsługuje rejestrację niestandardowego edytora, w której Edytor może zadeklarować koligację dla określonych rozszerzeń (na przykład. XAML i. RC) lub który jest odpowiedni dla dowolnego rozszerzenia (*). Począwszy od programu Visual Studio 2019 w wersji 16,1, rozszerzamy obsługę rejestracji edytora.

### <a name="filenames"></a>Nazwy plików

Oprócz lub zamiast, rejestrowania obsługi dla określonego rozszerzenia pliku, Edytor może zarejestrować, że obsługuje określone nazwy plików, stosując nowy `ProvideEditorFilename` atrybut do pakietu edytora.

Na przykład edytor obsługujący wszystkie pliki JSON zastosuje ten `ProvideEditorExtension` atrybut do jego pakietu:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Począwszy od 16,1, jeśli element webedit obsługuje tylko kilka dobrze znanych plików. JSON, można zamiast tego zastosować te `ProvideEditorFilename` atrybuty do pakietu:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Elementów UICONTEXT

Edytor może zarejestrować co najmniej jeden elementów UICONTEXT, który reprezentuje, gdy jest włączony. Elementów UICONTEXT są rejestrowane przez zastosowanie jednego lub większej liczby wystąpień `ProvideEditorUIContextAttribute` do pakietu, który rejestruje Edytor.

Jeśli Edytor zarejestrował elementów UICONTEXT:

- Jeśli co najmniej jeden z zarejestrowanych elementów UICONTEXT jest aktywny, gdy plik z danym rozszerzeniem zostanie otwarty, Edytor zostanie uwzględniony w przeszukiwaniu edytora.
- Jeśli żadna z zarejestrowanych elementów UICONTEXT nie jest aktywna, Edytor nie jest uwzględniany w wyszukiwaniu edytora.

Jeśli Edytor nie rejestruje żadnych elementów UICONTEXT, zawsze jest zawarty w edytorze wyszuka tego rozszerzenia.

Na przykład, jeśli edytor jest dostępny tylko wtedy, gdy projekt C# jest otwarty, można zadeklarować tę koligację przez zastosowanie `ProvideEditorUIContext` atrybutu:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
