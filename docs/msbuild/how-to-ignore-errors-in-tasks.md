---
title: 'Instrukcje: ignorowanie błędów w zadaniach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: abd907e86a451ca035d44d9a12084c7b84acd1ed
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777897"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Instrukcje: ignorowanie błędów w zadaniach
Czasami, gdy kompilacja ma być odporna na błędy w niektórych zadaniach. Jeśli te zadania niekrytyczne zakończą się niepowodzeniem, chcesz, aby kompilacja kontynuowała działanie, ponieważ nadal może generować wymagane dane wyjściowe. Na przykład, jeśli projekt używa zadania `SendMail` do wysłania wiadomości e-mail po skompilowaniu każdego składnika, można rozważyć zaakceptowanie, że kompilacja będzie kontynuowała pracę, nawet jeśli serwery poczty są niedostępne i nie można wysłać komunikatów o stanie. Jeśli na przykład pliki pośrednie są zazwyczaj usuwane podczas kompilacji, można rozważyć zaakceptowanie, aby kompilacja kontynuowała wykonywanie nawet wtedy, gdy te pliki nie mogą zostać usunięte.

## <a name="use-the-continueonerror-attribute"></a>Użyj atrybutu ContinueOnError
Atrybut `ContinueOnError` elementu `Task` kontroluje, czy kompilacja zatrzyma się czy kontynuuje, gdy wystąpi błąd zadania. Ten atrybut określa również, czy błędy mają być traktowane jako błędy lub ostrzeżenia, gdy kompilacja będzie kontynuowana.

Atrybut `ContinueOnError` może zawierać jedną z następujących wartości:

- **WarnAndContinue** lub **true**. Gdy zadanie się nie powiedzie, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i Build są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.

- **ErrorAndContinue**. Gdy zadanie nie powiedzie się, kolejne zadania w elemencie `Target` i kompilacja nadal będą wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.

- **ErrorAndStop** lub **false** (wartość domyślna). Gdy zadanie nie powiedzie się, pozostałe zadania w elemencie `Target` i kompilacja nie są wykonywane, a cały element `Target` i kompilacja są uznawane za niepowodzenie.

Wersje .NET Framework przed 4,5 są obsługiwane tylko przez wartości `true` i `false`.

Wartość domyślna `ContinueOnError` jest `ErrorAndStop`. Jeśli ustawisz atrybut na `ErrorAndStop`, zachowanie jawne dla każdego, kto odczytuje plik projektu.

#### <a name="to-ignore-an-error-in-a-task"></a>Aby zignorować błąd w zadaniu

Użyj atrybutu `ContinueOnError` zadania. Na przykład:

```c#
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Przykład
Poniższy przykład kodu ilustruje, że element docelowy `Build` nadal działa i kompilacja jest uważana za sukces, nawet jeśli zadanie `Delete` nie powiedzie się.

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

## <a name="see-also"></a>Zobacz także
- [MSBuild](../msbuild/msbuild.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
