---
title: Indeksowanie obszaru roboczego w programie Visual Studio | Microsoft Docs
description: Dowiedz się więcej o indeksowaniu obszarów roboczych, które jest kolekcją i trwałym magazynem danych w celu obsługi zaawansowanych funkcji środowiska IDE dla obszaru roboczego otwartego folderu.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 6b5c069ce3ae993f2d2371bffae3ac58b286fa70
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877055"
---
# <a name="workspace-indexing"></a>Indeksowanie obszaru roboczego

W rozwiązaniu systemy projektów są odpowiedzialne za dostarczanie funkcji kompilowania, debugowania, przeszukiwania **symboli i** nie tylko. Systemy projektu mogą wykonać tę czynność, ponieważ rozumieją relację i możliwości plików w ramach projektu. Obszar roboczy [otwartego folderu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) wymaga tego samego wglądu w celu zapewnienia również rozbudowanych funkcji środowiska IDE. Kolekcja i trwały magazyn danych to proces nazywany indeksem obszaru roboczego. Te indeksowane dane można zbadać za pomocą zestawu asynchronicznych interfejsów API. Rozszerzalne mogą uczestniczyć w procesie indeksowania przez udostępnienie klasy <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> , które wiedzą, jak obsługiwać pewne typy plików.

## <a name="types-of-indexed-data"></a>Typy indeksowanych danych

Istnieją trzy rodzaje danych, które są indeksowane. Należy pamiętać, że typ oczekiwany przez skanery plików różni się od typu deserializowanego od indeksu.

|Dane|Typ skanera plików|Typ wyniku zapytania indeksu|Powiązane typy|
|--|--|--|--|
|Dokumentacja|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symbole|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> powinien być używany zamiast `IIndexWorkspaceService` zapytań|
|Wartości danych|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Wykonywanie zapytań o indeksowane dane

Istnieją dwa typy asynchroniczne dostępne do uzyskiwania dostępu do utrwalonych danych. Pierwszy z nich to <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Zapewnia on podstawowy dostęp do pojedynczego pliku `FileReferenceResult` i `FileDataResult` danych, a następnie buforuje wyniki. Druga z <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> nich nie korzysta z buforowania, ale umożliwia wykonywanie zapytań o więcej możliwości.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Uczestnictwo w indeksowaniu

Indeksowanie obszaru roboczego jest w przybliżeniu następująca:

1. Odnajdywanie i trwałość jednostek systemu plików w obszarze roboczym (tylko podczas początkowego skanowania otwarcia).
1. Dla każdego pliku zostanie wyświetlony monit o przeszukanie w poszukiwaniu plików o najwyższym priorytecie `FileReferenceInfo` .
1. Dla każdego pliku zostanie wyświetlony monit o przeszukanie w poszukiwaniu plików o najwyższym priorytecie `SymbolDefinition` .
1. Dla każdego pliku są zadawane pytania dla wszystkich dostawców `FileDataValue` .

Rozszerzenia mogą eksportować skaner, implementując `IWorkspaceProviderFactory<IFileScanner>` i eksportując typ za pomocą <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . `SupportedTypes`Argument atrybutu powinien mieć co najmniej jedną wartość z <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Przykładowy skaner można znaleźć w przykładowym [zestawie SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)programu vs.

> [!WARNING]
> Nie Eksportuj skanera plików, który obsługuje `FileScannerTypeConstants.FileScannerContentType` Typ. Jest ona używana wyłącznie w celach wewnętrznych firmy Microsoft.

W sytuacjach zaawansowanych rozszerzenie może dynamicznie obsługiwać dowolny zestaw typów plików. Zamiast MEF eksportowanie `IWorkspaceProviderFactory<IFileScanner>` , rozszerzenie może eksportować `IWorkspaceProviderFactory<IFileScannerProvider>` . Po rozpoczęciu indeksowania ten typ fabryki zostanie zaimportowany, skonkretyzowany i zostanie <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> wywołana metoda. `IFileScanner` wystąpienia obsługujące dowolną wartość z `FileScannerTpeConstants` będą honorowane, a nie tylko symbole.

## <a name="next-steps"></a>Następne kroki

* [Obszary robocze i usługi językowe](workspace-language-services.md) — informacje na temat integrowania usług językowych z obszarem roboczym otwartego folderu.
* [Kompilacja obszaru roboczego](workspace-build.md) — otwarty folder obsługuje systemy kompilacji, takie jak MSBuild i pliki reguł programu make.