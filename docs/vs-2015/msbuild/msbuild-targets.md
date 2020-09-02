---
title: Elementy docelowe programu MSBuild | Microsoft Docs
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
ms.openlocfilehash: c4cc8d9654fc2d277f0b7c69483ab46aa3209983
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157604"
---
# <a name="msbuild-targets"></a>Obiekty docelowe w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadania grupy są obiektami docelowymi w określonej kolejności i umożliwiają umieszczenie procesu kompilacji w mniejszych jednostkach. Na przykład jeden obiekt docelowy może usunąć wszystkie pliki w katalogu wyjściowym, aby przygotować się do kompilacji, podczas gdy inna kompiluje dane wejściowe dla projektu i umieszcza je w pustym katalogu. Aby uzyskać więcej informacji o zadaniach, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Deklarowanie celów w pliku projektu  
 Elementy docelowe są zadeklarowane w pliku projektu z elementem [docelowym](../msbuild/target-element-msbuild.md) . Na przykład poniższy kod XML tworzy element docelowy o nazwie konstrukcja, który następnie wywołuje zadanie CSC z typem elementu kompilowania.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Podobnie jak w przypadku właściwości programu MSBuild, można ponownie zdefiniować elementy docelowe. Przykład:  
  
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
 Elementy docelowe muszą być uporządkowane, jeśli dane wejściowe do jednego obiektu docelowego są zależne od danych wyjściowych innego obiektu docelowego. Istnieje kilka sposobów, aby określić kolejność, w której są uruchamiane obiekty docelowe.  
  
- Początkowe elementy docelowe  
  
- Domyślne elementy docelowe  
  
- Pierwszy element docelowy  
  
- Zależności docelowe  
  
- `BeforeTargets` i `AfterTargets` (MSBuild 4,0)  
  
  Element docelowy nigdy nie jest uruchamiany dwukrotnie podczas pojedynczej kompilacji, nawet jeśli kolejny element docelowy w kompilacji zależy od niej. Po uruchomieniu elementu docelowego jego udział w kompilacji jest zakończony.  
  
  Aby uzyskać szczegółowe informacje i uzyskać więcej informacji na temat docelowej kolejności kompilacji, zobacz [Target Order Build](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Przetwarzanie wsadowe docelowe  
 Element docelowy może mieć atrybut, `Outputs` który określa metadane w postaci% (Metadata). W takim przypadku MSBuild uruchamia element docelowy raz dla każdej unikatowej wartości metadanych, grupując lub "wsadowe" elementy, które mają tę wartość metadanych. Przykład:  
  
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
  
 przetwarza elementy odniesienia według ich metadanych RequiredTargetFramework. Wynik elementu docelowego wygląda następująco:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 Przetwarzanie wsadowe docelowe jest rzadko używane w rzeczywistych kompilacjach. Tworzenie wsadowe zadań jest bardziej popularne. Aby uzyskać więcej informacji, zobacz Tworzenie [pakietów wsadowych](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Kompilacje przyrostowe  
 Kompilacje przyrostowe to kompilacje, które są zoptymalizowane tak, aby obiekty docelowe z plikami wyjściowymi, które są aktualne w odniesieniu do odpowiadających im plików wejściowych, nie są wykonywane. Element docelowy może mieć zarówno `Inputs` `Outputs` atrybuty, jak i, wskazujące elementy, które element docelowy oczekuje jako dane wejściowe i jakie elementy są generowane jako dane wyjściowe.  
  
 Jeśli wszystkie elementy wyjściowe są aktualne, program MSBuild pomija element docelowy, co znacznie zwiększa szybkość kompilacji. Jest to nazywane kompilacją przyrostową docelowej. Jeśli tylko niektóre pliki są aktualne, program MSBuild wykonuje element docelowy bez aktualnych elementów. Ta nazwa jest nazywana częściową kompilacją przyrostową obiektu docelowego. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Instrukcje: Użycie tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
