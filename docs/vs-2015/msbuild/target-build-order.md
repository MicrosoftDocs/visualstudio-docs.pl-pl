---
title: Docelowa kompilacja — kolejność | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054447"
---
# <a name="target-build-order"></a>Kolejność kompilowania obiektów docelowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Muszą być uporządkowane obiekty docelowe, jeśli dane wejściowe do jednego obiektu docelowego jest zależna od danych wyjściowych z innym elementem docelowym. Aby określić kolejność uruchamiania elementów docelowych, można użyć tych atrybutów:  
  
- `InitialTargets`. To `Project` atrybut określa elementy docelowe, które będą uruchamiane po pierwsze, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w `DefaultTargets` atrybutu.  
  
- `DefaultTargets`. To `Project` atttribute Określa, które elementy docelowe są uruchamiane, jeśli element docelowy nie jest jawnie określona w wierszu polecenia.  
  
- `DependsOnTargets`. To `Target` atrybut określa elementy docelowe, które muszą zostać uruchomione przed uruchomieniem tego obiektu docelowego.  
  
- `BeforeTargets` i `AfterTargets`. Te `Target` atrybuty określają, że ten element docelowy powinien być wykonywany przed lub po określonych celów (MSBuild 4.0).  
  
  Obiekt docelowy nigdy nie jest uruchamiane dwa razy podczas kompilacji, nawet wtedy, gdy kolejne docelowego w kompilacji zależy od niego. Po uruchomieniu elementu docelowego swój wkład zgodnie z kompilacją zostało ukończone.  
  
  Obiekty docelowe może mieć `Condition` atrybutu. Jeśli określony warunek ma `false`, element docelowy nie jest wykonywane i nie ma wpływu na kompilację. Aby uzyskać więcej informacji o warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).  
  
## <a name="initial-targets"></a>Cele początkowe  
 `InitialTargets` Atrybutu [projektu](../msbuild/project-element-msbuild.md) element określa elementy docelowe, które będą uruchamiane po pierwsze, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w `DefaultTargets` atrybutu. Cele początkowe są zwykle używane do sprawdzania błędów.  
  
 Wartość `InitialTargets` atrybut może być rozdzielone średnikami, uporządkowanych lista elementów docelowych. Poniższy przykład określa, że `Warm` docelowy działa, a następnie `Eject` docelowych uruchomienia.  
  
```  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Importowany projektów może mieć własne `InitialTargets` atrybutów. Wszystkie cele początkowe są zagregowane ze sobą i są uruchamiane w kolejności.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Określanie pierwszego obiektu docelowego do kompilacji](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="default-targets"></a>Domyślne elementy docelowe  
 `DefaultTargets` Atrybutu [projektu](../msbuild/project-element-msbuild.md) element określa, których cel lub cele są tworzone, jeśli element docelowy nie jest jawnie określona w wierszu polecenia.  
  
 Wartość `DefaultTargets` atrybut może być rozdzielaną średnikami, uporządkowaną listę domyślnych elementów docelowych. Poniższy przykład określa, że `Clean` docelowy działa, a następnie `Build` docelowych uruchomienia.  
  
```  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Można zastąpić domyślne elementy docelowe za pomocą **/target** Przejdź w wierszu polecenia. Poniższy przykład określa, że `Build` docelowy działa, a następnie `Report` docelowych uruchomienia. Po określeniu elementów docelowych w ten sposób wszystkie domyślne elementy docelowe są ignorowane.  
  
 `msbuild /target:Build;Report`  
  
 Jeśli określono zarówno cele początkowe i domyślne elementy docelowe, a jeśli nie określono żadnych elementów docelowych w wiersza polecenia, MSBuild uruchamia cele początkowe najpierw, a następnie uruchomić domyślnych elementów docelowych.  
  
 Importowany projektów może mieć własne `DefaultTargets` atrybutów. Pierwszy `DefaultTargets` napotkano atrybut określa, które domyślne elementy docelowe zostanie uruchomiony.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Określanie pierwszego obiektu docelowego do kompilacji](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="first-target"></a>Pierwszy element docelowy  
 Jeśli nie ma żadnych cele początkowe, domyślne elementy docelowe ani wiersza polecenia obiekty docelowe, MSBuild uruchamia pierwszego obiektu docelowego napotka w pliku projektu lub jakiegokolwiek projektu, zaimportowane pliki.  
  
## <a name="target-dependencies"></a>Miejsce docelowe zależności  
 Obiekty docelowe można opisać relacji zależności ze sobą. `DependsOnTargets` Atrybut wskazuje, że obiekt docelowy zależy od innych elementów docelowych. Na przykład  
  
```  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 informuje o MSBuild `Serve` zależy obiekt docelowego `Chop` docelowego i `Cook` docelowej. MSBuild uruchamia `Chop` docelowego, a następnie uruchamia `Cook` docelowy przed uruchomieniem `Serve` docelowej.  
  
## <a name="beforetargets-and-after-targets"></a>BeforeTargets i po obiektach docelowych  
 W wersji 4.0 programu MSBuild, należy określić kolejność obiektów docelowych za pomocą `BeforeTargets` i `AfterTargets` atrybutów.  
  
 Rozważmy poniższy skrypt.  
  
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
  
 Do utworzenia obiektu docelowego pośrednich `Optimize` , które jest uruchamiane `Compile` docelowej, lecz przed `Link` obiekt docelowy, Dodaj następujący element docelowy gdziekolwiek w `Project` elementu.  
  
```  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## <a name="determining-the-target-build-order"></a>Określenie kolejności kompilacji docelowej  
 MSBuild określa kolejność kompilowania obiektów docelowych w następujący sposób:  
  
1. `InitialTargets` obiekty docelowe są uruchamiane.  
  
2. Cele określone w wierszu polecenia przez **/target** przełącznika są uruchamiane. Jeśli określisz żadnych elementów docelowych w wierszu polecenia, a następnie `DefaultTargets` obiekty docelowe są uruchamiane. Jeśli nie jest obecny, pierwszy napotkano element docelowy zostanie uruchomiony.  
  
3. `Condition` Atrybut docelowy jest oceniany. Jeśli `Condition` atrybut jest obecny i daje w wyniku `false`, element docelowy nie jest wykonywane i nie ma dalszych wpływu na kompilację.  
  
4. Przed wykonaniem celu jego `DependsOnTargets` obiekty docelowe są uruchamiane.  
  
5. Przed wykonaniem celu dowolnej docelowej, jest wyświetlany w `BeforeTargets` atrybutu jest uruchamiany.  
  
6. Przed wykonaniem celu jego `Inputs` atrybutu i `Outputs` atrybutu są porównywane. Jeśli program MSBuild ustali, że wszystkie pliki wyjściowe są nieaktualne w odniesieniu do odpowiedniego pliku wejściowego lub pliki, a następnie program MSBuild wykonuje element docelowy. W przeciwnym razie program MSBuild pomija element docelowy.  
  
7. Po obiekt docelowy jest wykonywany czy pomijany, wszelkie docelowy, który jest wyświetlany w `AfterTargets` atrybutu jest uruchamiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Docelowe elementy](../msbuild/msbuild-targets.md)
