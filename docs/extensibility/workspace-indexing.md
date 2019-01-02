---
title: Obszar roboczy indeksowania w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 90722b540fd0569ab54ff945f5c1caa43668dccf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899746"
---
# <a name="workspace-indexing"></a>Indeksowanie obszaru roboczego

W rozwiązaniu systemów projektu jest odpowiedzialny za dostarczanie funkcji dla kompilacji, debugowania, **GoTo** wyszukiwania symboli i nie tylko. Systemy projektu mogą wykonać to zadanie, ponieważ rozumieją relacji i możliwości pliki w projekcie. [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) obszaru roboczego wymaga takiego samego wglądu, aby zapewnić rozbudowane środowisko IDE funkcji, jak również. Zbieranie i z magazynu trwałego tych danych jest w procesie zwanym indeksowania obszaru roboczego. Indeksowane dane mogą być przeszukiwane przy użyciu zestawu asynchronicznych interfejsów API. Urządzenia Extender mogą uczestniczyć w procesie indeksowania, zapewniając <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>s, wiesz, że sposób obsługi niektórych typów plików.

## <a name="types-of-indexed-data"></a>Typy indeksowane dane

Istnieją trzy rodzaje danych, które są indeksowane. Należy zauważyć, że typ oczekiwany ze skanerów pliku różni się od typu deserializacji z indeksu.

|Dane|Typ skanera pliku|Typ wyniku zapytania indeksu|Powiązanych typów|
|--|--|--|--|
|Odwołania|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symbole|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> należy użyć zamiast `IIndexWorkspaceService` zapytań|
|Wartości danych|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Wykonanie zapytania dotyczącego indeksowane dane

Istnieją dwa typy asynchronicznego umożliwiających dostęp do danych. Pierwsza to za pośrednictwem <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Zapewnia podstawowe dostęp do jednego pliku `FileReferenceResult` i `FileDataResult` danych i zapisuje w pamięci podręcznej wyników. Drugi to <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> który nie korzysta z pamięci podręcznej, ale umożliwia więcej możliwości zapytań.

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

## <a name="participating-in-indexing"></a>Udział w indeksowaniu

Poniższa sekwencja około indeksowania obszaru roboczego są następujące:

1. Odnajdywanie i trwałość obiektów systemowych plików w obszarze roboczym (tylko na otwieranie początkowego skanowania).
1. Na plik, pasującego dostawcy z najwyższym priorytetem jest proszony o skanowania w poszukiwaniu `FileReferenceInfo`s.
1. Na plik, pasującego dostawcy z najwyższym priorytetem jest proszony o skanowania w poszukiwaniu `SymbolDefinition`s.
1. Na plik, wszyscy dostawcy monit o podanie `FileDataValue`s.

Rozszerzenia można wyeksportować skaner implementując `IWorkspaceProviderFactory<IFileScanner>` i eksportowanie typu za pomocą <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. `SupportedTypes` Argument atrybutu musi być co najmniej jedną wartość z <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Skanera przykład zobacz zestaw SDK programu VS [przykładowe](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Nie Eksportuj skaner pliku, który obsługuje `FileScannerTypeConstants.FileScannerContentType` typu. Służy do firmy Microsoft, tylko wewnętrznie.

W sytuacjach zaawansowane rozszerzenia dynamicznie może obsługiwać dowolny zestaw typów plików. Zamiast eksportu MEF `IWorkspaceProviderFactory<IFileScanner>`, można wyeksportować rozszerzenie `IWorkspaceProviderFactory<IFileScannerProvider>`. Po rozpoczęciu indeksowanie tego typu fabryki zostanie zaimportowany, uruchomiony i mają jego <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> wywołana metoda. `IFileScanner` Obsługa dowolną wartość z wystąpienia `FileScannerTpeConstants` będzie uznawany, nie tylko symbole.

## <a name="next-steps"></a>Następne kroki

* [Obszary robocze i usług językowych](workspace-language-services.md) — informacje o sposobie integrowania usług językowych z obszarem roboczym otwórz Folder.
* [Obszar roboczy kompilacji](workspace-build.md) — funkcja otwierania folderu obsługuje tworzenie systemów, takich jak MSBuild i pliki reguł programu make.