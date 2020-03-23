---
title: 'Jak: Ignorowanie błędów w zadaniach | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 9899b7367e6ae9255755ae04fe06d8c8733043ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633827"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Jak: Ignorowanie błędów w zadaniach

Czasami chcesz, aby kompilacja była tolerancyjna dla błędów w niektórych zadaniach. Jeśli te zadania nie krytyczne nie powiedzie się, chcesz, aby kompilacja była kontynuowana, ponieważ nadal może tworzyć wymagane dane wyjściowe. Na przykład jeśli projekt używa `SendMail` zadania do wysyłania wiadomości e-mail po każdym składniku jest zbudowany, można uznać za dopuszczalne dla kompilacji, aby przejść do ukończenia, nawet wtedy, gdy serwery poczty są niedostępne i wiadomości o stanie nie mogą być wysyłane. Lub, na przykład, jeśli pliki pośrednie są zwykle usuwane podczas kompilacji, można uznać za dopuszczalne dla kompilacji, aby przejść do zakończenia, nawet jeśli te pliki nie mogą zostać usunięte.

## <a name="use-the-continueonerror-attribute"></a>Użyj atrybutu ContinueOnError

Atrybut `ContinueOnError` `Task` elementu określa, czy kompilacja zatrzymuje się lub kontynuuje, gdy wystąpi błąd zadania. Ten atrybut kontroluje również, czy błędy są traktowane jako błędy lub ostrzeżenia, gdy kompilacja jest kontynuowana.

Atrybut `ContinueOnError` może zawierać jedną z następujących wartości:

- **WarnAndKontynuuj** lub **prawda**. Gdy zadanie nie powiedzie się, kolejne zadania w [target](../msbuild/target-element-msbuild.md) element i kompilacji nadal wykonywać, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.

- **ErrorAndContinue**. Gdy zadanie nie powiedzie `Target` się, kolejne zadania w elemencie i kompilacji nadal wykonywać, a wszystkie błędy z zadania są traktowane jako błędy.

- **ErrorAndStop** lub **false** (domyślnie). Gdy zadanie zakończy się niepowodzeniem, pozostałe zadania w `Target` elemencie `Target` i kompilacji nie są wykonywane, a cały element i kompilacja jest uważany za nie powiodło się.

Wersje programu .NET Framework przed 4.5 `true` `false` obsługiwane tylko i wartości.

Wartością `ContinueOnError` domyślną `ErrorAndStop`jest . Jeśli ustawisz atrybut `ErrorAndStop`, należy jawić zachowanie dla każdego, kto czyta plik projektu.

#### <a name="to-ignore-an-error-in-a-task"></a>Aby zignorować błąd w zadaniu

Użyj `ContinueOnError` atrybutu zadania. Przykład:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje, że obiekt docelowy `Build` nadal działa, a kompilacja jest uważana za powodzenie, nawet jeśli zadanie zakończy się niepowodzeniem. `Delete`

```xml
<Project DefaultTargets="FakeBuild"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Files Include="*.obj"/>
    </ItemGroup>
    <Target Name="Clean">
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
    </Target>

    <Target Name="FakeBuild" DependsOnTargets="Clean">
        <Message Text="Building after cleaning..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Msbuild](../msbuild/msbuild.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
