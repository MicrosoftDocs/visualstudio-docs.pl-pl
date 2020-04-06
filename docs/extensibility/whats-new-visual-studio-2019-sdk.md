---
title: Co nowego w SDK programu Visual Studio 2019 | Dokumenty firmy Microsoft
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740401"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Co nowego w sdk programu Visual Studio 2019

Visual Studio SDK ma następujące nowe i zaktualizowane funkcje programu Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Synchroniczne automatyczne ładowanie rozszerzeń ostrzeżenie

Użytkownicy zobaczą teraz ostrzeżenie, jeśli którekolwiek z zainstalowanych rozszerzeń jest synchronicznie automatycznie ładowane podczas uruchamiania. Więcej informacji na temat ostrzeżenia można uzyskać w u [synchronicznie z automatycznym ładowaniem rozszerzeń.](synchronously-autoloaded-extensions.md)

## <a name="single-unified-visual-studio-sdk"></a>Pojedynczy, ujednolicony visual studio SDK

Teraz można uzyskać wszystkie zasoby zestawu SDK programu Visual Studio za pośrednictwem jednego pakietu NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Ulepszenia rejestracji edytora

Od momentu utworzenia programu Visual Studio obsługuje niestandardową rejestrację edytora, w której edytor może deklarować koligacji dla określonych rozszerzeń (na przykład .xaml i .rc) lub że jest odpowiedni dla dowolnego rozszerzenia (.*). Począwszy od programu Visual Studio 2019 w wersji 16.1, możemy rozszerzyć obsługę rejestracji edytora.

### <a name="filenames"></a>Nazwy plików

Oprócz lub zamiast rejestrowania obsługi dla określonego rozszerzenia pliku, edytor może zarejestrować, że obsługuje określone nazwy `ProvideEditorFilename` plików, stosując nowy atrybut do pakietu edytora.

Na przykład edytor, który obsługuje wszystkie pliki `ProvideEditorExtension` json będzie stosować ten atrybut do swojego pakietu:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Począwszy od 16.1, jeśli MyEditor obsługuje tylko kilka dobrze znanych plików .json, może zamiast tego zastosować te `ProvideEditorFilename` atrybuty do swojego pakietu:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Konteksty interfejsu użytkownika

Edytor może zarejestrować jeden lub więcej UIContexts, które reprezentują, gdy jest włączona. UIContexts są rejestrowane przez zastosowanie jednego `ProvideEditorUIContextAttribute` lub więcej wystąpień do pakietu, który rejestruje edytora.

Jeśli edytor zarejestrował UIContexts:

- Jeśli co najmniej jeden z zarejestrowanych UIContexts jest aktywny po otwarciu pliku z danym rozszerzeniem, edytor jest uwzględniony w wyszukiwarce edytora.
- Jeśli żaden z zarejestrowanych UIContexts jest aktywny, edytor nie jest uwzględniony w wyszukiwarce edytora.

Jeśli edytor nie rejestruje żadnych UIContexts, zawsze jest uwzględniony w wyszukiwaniu edytora dla tego rozszerzenia.

Na przykład jeśli edytor jest dostępny tylko wtedy, gdy projekt języka C# jest `ProvideEditorUIContext` otwarty, może zadeklarować tę koligacji, stosując atrybut:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
