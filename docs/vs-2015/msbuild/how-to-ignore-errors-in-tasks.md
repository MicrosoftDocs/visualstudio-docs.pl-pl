---
title: 'Instrukcje: ignorowanie błędów w zadaniach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5025cc3e9dc0e13c3ae4658d129f5d0ac94f6fd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156596"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Porady: ignorowanie błędów w zadaniach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami, gdy kompilacja ma być odporna na błędy w niektórych zadaniach. Jeśli te zadania niekrytyczne zakończą się niepowodzeniem, chcesz, aby kompilacja kontynuowała działanie, ponieważ nadal może generować wymagane dane wyjściowe. Na przykład, jeśli projekt używa `SendMail` zadania do wysłania wiadomości e-mail po skompilowaniu każdego składnika, można rozważyć, że może on zostać zaakceptowany do ukończenia kompilacji, nawet jeśli serwery poczty są niedostępne i nie można wysłać komunikatów o stanie. Jeśli na przykład pliki pośrednie są zazwyczaj usuwane podczas kompilacji, można rozważyć zaakceptowanie, aby kompilacja kontynuowała wykonywanie nawet wtedy, gdy te pliki nie mogą zostać usunięte.  
  
## <a name="using-the-continueonerror-attribute"></a>Korzystanie z atrybutu ContinueOnError  
 `ContinueOnError`Atrybut `Task` elementu określa, czy kompilacja jest zatrzymywana czy kontynuowana, gdy wystąpi błąd zadania. Ten atrybut określa również, czy błędy mają być traktowane jako błędy lub ostrzeżenia, gdy kompilacja będzie kontynuowana.  
  
 `ContinueOnError`Atrybut może zawierać jedną z następujących wartości:  
  
- **WarnAndContinue** lub **true**. Gdy zadanie się nie powiedzie, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i Build są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.  
  
- **ErrorAndContinue**. Gdy zadanie nie powiedzie się, kolejne zadania w `Target` elemencie i kompilacja będą nadal wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.  
  
- **ErrorAndStop** lub **false** (wartość domyślna). Jeśli zadanie nie powiedzie się, pozostałe zadania w `Target` elemencie i kompilacja nie są wykonywane, a cały `Target` element i kompilacja są uważane za zakończone niepowodzeniem.  
  
  Wersje .NET Framework przed 4,5 obsługiwane tylko `true` `false` wartości i.  
  
  Wartość domyślna `ContinueOnError` to `ErrorAndStop` . W przypadku ustawienia atrybutu na `ErrorAndStop` , należy jawnie wprowadzić zachowanie dla każdej osoby, która odczytuje plik projektu.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Aby zignorować błąd w zadaniu  
  
- Użyj `ContinueOnError` atrybutu zadania. Na przykład:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje, że `Build` element docelowy nadal działa i kompilacja jest uważana za sukces, nawet jeśli `Delete` zadanie nie powiedzie się.  
  
```  
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
[MSBuild](msbuild.md)  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
