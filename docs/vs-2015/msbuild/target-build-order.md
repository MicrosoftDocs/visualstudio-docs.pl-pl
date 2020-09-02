---
title: Docelowy porządek kompilacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ea2068bce101eb27a81da4925e0fef6ffa8c534
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144276"
---
# <a name="target-build-order"></a>Kolejność kompilowania obiektów docelowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Elementy docelowe muszą być uporządkowane, jeśli dane wejściowe do jednego obiektu docelowego są zależne od danych wyjściowych innego obiektu docelowego. Można użyć tych atrybutów do określenia kolejności, w której są uruchamiane obiekty docelowe:  
  
- `InitialTargets`. Ten `Project` atrybut określa elementy docelowe, które będą uruchamiane jako pierwsze, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w `DefaultTargets` atrybucie.  
  
- `DefaultTargets`. Ta `Project` atrybut określa, które obiekty docelowe są uruchamiane, jeśli element docelowy nie zostanie określony jawnie w wierszu polecenia.  
  
- `DependsOnTargets`. Ten `Target` atrybut określa elementy docelowe, które muszą zostać uruchomione, aby można było uruchomić ten element docelowy.  
  
- `BeforeTargets` i `AfterTargets` . Te `Target` atrybuty określają, że ten element docelowy powinien zostać uruchomiony przed lub po określonych obiektach docelowych (MSBuild 4,0).  
  
  Element docelowy nigdy nie jest uruchamiany dwukrotnie podczas kompilacji, nawet jeśli kolejny element docelowy w kompilacji zależy od niej. Po uruchomieniu elementu docelowego jego udział w kompilacji jest zakończony.  
  
  Elementy docelowe mogą mieć `Condition` atrybut. Jeśli określony warunek ma wartość `false` , element docelowy nie zostanie wykonany i nie ma wpływu na kompilację. Aby uzyskać więcej informacji o warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).  
  
## <a name="initial-targets"></a>Cele początkowe  
 `InitialTargets`Atrybut elementu [projektu](../msbuild/project-element-msbuild.md) określa elementy docelowe, które będą uruchamiane jako pierwsze, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w `DefaultTargets` atrybucie. Początkowe cele są zwykle używane do sprawdzania błędów.  
  
 Wartością `InitialTargets` atrybutu może być rozdzielana średnikami lista elementów docelowych. W poniższym przykładzie określono, że `Warm` obiekt docelowy jest uruchamiany, a następnie `Eject` jest uruchamiany element docelowy.  
  
```  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Importowane projekty mogą mieć własne `InitialTargets` atrybuty. Wszystkie początkowe elementy docelowe są agregowane i uruchamiane w kolejności.  
  
 Aby uzyskać więcej informacji, zobacz [How to: Określ, który element docelowy należy skompilować jako pierwszy](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="default-targets"></a>Domyślne elementy docelowe  
 `DefaultTargets`Atrybut elementu [projektu](../msbuild/project-element-msbuild.md) określa, które elementy docelowe lub docelowe są kompilowane, jeśli element docelowy nie został jawnie określony w wierszu polecenia.  
  
 Wartością `DefaultTargets` atrybutu może być rozdzielana średnikami lista domyślnych elementów docelowych. W poniższym przykładzie określono, że `Clean` obiekt docelowy jest uruchamiany, a następnie `Build` jest uruchamiany element docelowy.  
  
```  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Domyślne obiekty docelowe można przesłonić przy użyciu przełącznika **/Target** w wierszu polecenia. W poniższym przykładzie określono, że `Build` obiekt docelowy jest uruchamiany, a następnie `Report` jest uruchamiany element docelowy. Gdy określisz elementy docelowe w ten sposób, wszystkie domyślne elementy docelowe zostaną zignorowane.  
  
 `msbuild /target:Build;Report`  
  
 Jeśli określono zarówno początkowe elementy docelowe, jak i domyślne elementy docelowe, a jeśli nie określono elementów docelowych wiersza polecenia, program MSBuild najpierw uruchamia początkowe elementy docelowe, a następnie uruchamia domyślne elementy docelowe.  
  
 Importowane projekty mogą mieć własne `DefaultTargets` atrybuty. Podczas pierwszego `DefaultTargets` napotkanego atrybutu określa się, które domyślne elementy docelowe zostaną uruchomione.  
  
 Aby uzyskać więcej informacji, zobacz [How to: Określ, który element docelowy należy skompilować jako pierwszy](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="first-target"></a>Pierwszy element docelowy  
 Jeśli nie ma początkowych elementów docelowych, domyślnych obiektów docelowych lub obiektów docelowych wiersza polecenia, program MSBuild uruchamia pierwszy element docelowy napotkany w pliku projektu lub zaimportowanych plikach projektu.  
  
## <a name="target-dependencies"></a>Miejsce docelowe zależności  
 Obiekty docelowe mogą opisywać relacje zależności ze sobą. Ten `DependsOnTargets` atrybut wskazuje, że element docelowy zależy od innych elementów docelowych. Przykład:  
  
```  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 informuje program MSBuild, że `Serve` element docelowy zależy od `Chop` elementu docelowego i `Cook` celu. Program MSBuild uruchamia `Chop` obiekt docelowy, a następnie uruchamia `Cook` obiekt docelowy przed uruchomieniem `Serve` obiektu docelowego.  
  
## <a name="beforetargets-and-after-targets"></a>BeforeTargets i After targets  
 W programie MSBuild 4,0 można określić kolejność obiektów docelowych przy użyciu `BeforeTargets` atrybutów i `AfterTargets` .  
  
 Rozważmy następujący skrypt.  
  
```  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 Aby utworzyć pośredni cel, `Optimize` który jest uruchamiany po `Compile` elemencie docelowym, ale przed `Link` elementem docelowym, Dodaj następujący element docelowy gdziekolwiek w `Project` elemencie.  
  
```  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## <a name="determining-the-target-build-order"></a>Określenie kolejności kompilacji docelowej  
 Program MSBuild określa docelowy porządek kompilacji w następujący sposób:  
  
1. `InitialTargets` elementy docelowe są uruchamiane.  
  
2. Elementy docelowe określone w wierszu polecenia przez przełącznik **/Target** są uruchamiane. Jeśli w wierszu polecenia nie określono żadnych elementów docelowych, `DefaultTargets` zostaną uruchomione obiekty docelowe. Jeśli żaden z nich nie jest obecny, zostanie uruchomiony pierwszy element docelowy.  
  
3. `Condition`Atrybut elementu docelowego jest obliczany. Jeśli `Condition` atrybut jest obecny i szacuje się `false` , obiekt docelowy nie jest wykonywany i nie ma żadnego wpływu na kompilację.  
  
4. Przed wykonaniem elementu docelowego, jego `DependsOnTargets` obiekty docelowe są uruchamiane.  
  
5. Przed wykonaniem elementu docelowego, każdy element docelowy, który wyświetla go w `BeforeTargets` atrybucie jest uruchamiany.  
  
6. Przed wykonaniem elementu docelowego jego `Inputs` atrybut i `Outputs` atrybut są porównywane. Jeśli program MSBuild ustali, że wszystkie pliki wyjściowe są nieaktualne w odniesieniu do odpowiedniego pliku lub plików wejściowych, MSBuild wykonuje miejsce docelowe. W przeciwnym razie program MSBuild pomija element docelowy.  
  
7. Po wykonaniu lub pominięciu elementu docelowego, każdy element docelowy, który wyświetla go w `AfterTargets` atrybucie jest uruchamiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)
