---
title: What's New in Visual Studio SDK 2019 r | Dokumentacja firmy Microsoft
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: daa4203ccdcbce89f1eb09efdd9433210bcbc987
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58856648"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>What's New in Visual Studio SDK 2019 r

Visual Studio SDK zawiera następujące nowe i zaktualizowane funkcje dla programu Visual Studio 2019 r.

## <a name="synchronously-autoloaded-extensions-warning"></a>Synchronicznie rozszerzenia załadowany automatycznie ostrzeżenie

Użytkownicy zobaczą teraz ostrzeżenie, jeśli ich zainstalowanych rozszerzeń są synchroniczne załadowany automatycznie podczas uruchamiania. Dowiedz się więcej o ostrzeżenie na [synchronicznie załadowany automatycznie rozszerzenia](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Pojedynczą, jednolitą programu Visual Studio SDK

Teraz możesz uzyskać wszystkie zasoby z zestawu SDK programu Visual Studio za pośrednictwem jednego pakietu NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Udoskonalenia w zakresie rejestracji edytora

Od jego utworzenia programu Visual Studio ma obsługiwane rejestracji niestandardowego edytora której edytora można zadeklarować jego koligacji dla określonego rozszerzenia (na przykład .xaml i .rc) lub jest ona odpowiednia dla dowolnego rozszerzenia (. *). Począwszy od programu Visual Studio 2019 wersji 16.1, możemy rozszerzyć obsługę rejestracji edytora.

### <a name="filenames"></a>Nazwy plików

Oprócz lub zamiast rejestrowanie pomocy technicznej dla konkretnego rozszerzenia pliku edytora można zarejestrować obsługuje określone nazwy plików, stosując nowy `ProvideEditorFilename` atrybutu do edytora pakietu.

Na przykład czy zastosować Edytor który obsługuje wszystkie pliki JSON to `ProvideEditorExtension` atrybutu do pakietu:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Począwszy 16.1, jeśli MyEditor obsługuje tylko kilka plików JSON dobrze znanego, możliwość zamiast stosowania tych `ProvideEditorFilename` atrybuty do pakietu:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Elementów Uicontext

Edytor można zarejestrować jeden lub więcej elementów Uicontext, które reprezentują, gdy jest włączone. Elementów Uicontext są rejestrowane przez zastosowanie jednego lub większej liczby wystąpień `ProvideEditorUIContextAttribute` do pakietu, który rejestruje edytora.

Jeśli Edytor ma zarejestrowanych elementów Uicontext:

- Jeśli co najmniej jeden z jego zarejestrowanych elementów Uicontext jest aktywny, po otwarciu pliku z rozszerzeniem danego, edytora znajduje się w polu wyszukiwania edytora.
- Jeśli żaden z zarejestrowanych elementów Uicontext nie jest aktywne, edytora jest niedostępna w wyszukiwaniu edytora.

Jeśli żadnych elementów Uicontext nie rejestrować się w edytorze, jest on zawsze uwzględniany w wyszukiwaniu edytora dla tego rozszerzenia.

Na przykład, jeśli edytor jest dostępna tylko podczas C# projekt był otwarty, jego można zadeklarować tego koligacji, stosując `ProvideEditorUIContext` atrybutu:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```