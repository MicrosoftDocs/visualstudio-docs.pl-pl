---
title: Elementy docelowe programu MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06b49a8fda448707540d5bfe65d0499c6c2dde96
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767366"
---
# <a name="msbuild-targets"></a>Obiekty docelowe w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Obiekty docelowe grupują zadania w określonej kolejności i pozwól, aby być uwzględniona na mniejsze jednostki proces kompilacji. Na przykład jeden element docelowy może usunąć wszystkie pliki w katalogu wyjściowym, aby przygotować się do kompilacji, podczas gdy inny kompiluje dane wejściowe dla projektu i umieszcza je w pusty katalog. Aby uzyskać więcej informacji na temat zadań, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Deklarowanie obiektów docelowych w pliku projektu  
 Obiekty docelowe są deklarowane w pliku projektu za pomocą [docelowej](../msbuild/target-element-msbuild.md) elementu. Na przykład następujący kod XML tworzy obiekt docelowy o nazwie konstrukcji, która następnie wywołuje CSC — zadanie z typem elementu kompilacji.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Podobnie jak właściwości programu MSBuild można ponownie zdefiniować cele. Na przykład  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Jeśli AfterBuild wykonuje, wyświetla tylko "drugie wystąpienie".  
  
## <a name="target-build-order"></a>Kolejność kompilowania obiektów docelowych  
 Muszą być uporządkowane obiekty docelowe, jeśli dane wejściowe do jednego obiektu docelowego jest zależna od danych wyjściowych z innym elementem docelowym. Istnieje kilka sposobów, aby określić kolejność, w które elementy docelowe, uruchom.  
  
- Cele początkowe  
  
- Domyślne elementy docelowe  
  
- Pierwszy element docelowy  
  
- Miejsce docelowe zależności  
  
- `BeforeTargets` i `AfterTargets` (MSBuild 4.0)  
  
  Obiekt docelowy nigdy nie będzie uruchamiany dwa razy podczas pojedynczej kompilacji, nawet wtedy, gdy kolejne docelowego w kompilacji zależy od niego. Po uruchomieniu elementu docelowego swój wkład zgodnie z kompilacją zostało ukończone.  
  
  Aby uzyskać szczegóły i dodatkowe informacje o docelowym kolejność kompilacji, zobacz [kolejności kompilacji docelowej](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Przetwarzaniu wsadowym obiektów docelowych  
 Element docelowy może mieć `Outputs` atrybut, który określa metadanych w formie % (metadane). Jeśli tak, MSBuild uruchamia docelowej jeden raz dla każdej wartości unikatowe metadane, grupowania lub "przetwarzanie wsadowe" elementy, które mają tę wartość metadanych. Na przykład  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 Przywoływanie elementów według ich metadanych RequiredTargetFramework partie. Dane wyjściowe w element docelowy wygląda następująco:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 Przetwarzaniu wsadowym obiektów docelowych rzadko jest używany w kompilacjach do rzeczywistego. Przetwarzanie wsadowe zadań jest bardziej powszechne. Aby uzyskać więcej informacji, zobacz [przetwarzania wsadowego](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Kompilacje przyrostowe  
 Kompilacje przyrostowe to kompilacje, które są zoptymalizowane pod kątem tak, aby obiekty docelowe z pliki wyjściowe są aktualne w odniesieniu do odpowiadające im pliki wejściowe nie są wykonywane. Element docelowy może mieć jednocześnie `Inputs` i `Outputs` atrybutów, wskazujące elementy docelowego wartością wejściową, a elementy generowane jako dane wyjściowe.  
  
 Jeśli wszystkie elementy wyjściowe są aktualne, program MSBuild pomija element docelowy, co znacznie zwiększa szybkość kompilacji. Jest to kompilacja przyrostowa, obiektu docelowego. Jeśli tylko niektóre pliki są aktualne, program MSBuild wykonuje element docelowy bez elementy aktualne. Jest to nazywane częściową kompilacją przyrostową elementu docelowego. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Instrukcje: Użyj tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
