---
title: Opcje użytkownika rozwiązania (. Suo) Plik | Microsoft Docs
description: Dowiedz się więcej o pliku opcji użytkownika rozwiązania (suo), który zawiera opcje rozwiązań dla 1 użytkownika w pliku magazynu strukturalnego przechowywanym w formacie binarnym.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a38eb865cf003f7a2f9bafde7b6e527ce24f2bd
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899618"
---
# <a name="solution-user-options-suo-file"></a>Plik opcji użytkownika rozwiązania (Suo)
Plik opcji użytkownika rozwiązania (suo) zawiera opcje rozwiązania dla 1 użytkownika. Tego pliku nie należy zaewidencjonować do kontroli kodu źródłowego.

 Plik opcji użytkownika rozwiązania (suo) jest magazynem strukturalnym, czyli plikiem złożonym, przechowywanym w formacie binarnym. Informacje o użytkowniku są zapisywane w strumieniach z nazwą strumienia będącą kluczem, który będzie używany do identyfikowania informacji w pliku .suo. Plik opcji użytkownika rozwiązania służy do przechowywania ustawień preferencji użytkownika i jest tworzony automatycznie podczas Visual Studio zapisania rozwiązania.

 Gdy środowisko otwiera plik suo, wylicza wszystkie aktualnie załadowane pakiet VSPackages. Jeśli pakiet VSPackage implementuje interfejs, środowisko wywołuje metodę w pniu VSPackage z prośbą o załadowanie wszystkich danych z pliku <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> .suo.

 Pakiet VSPackage jest odpowiedzialny za to, jakie strumienie mogły zostać zapisane w pliku suo. Dla każdego strumienia, który napisał, pakiet VSPackage wywołuje z powrotem do środowiska za pośrednictwem , aby załadować określony strumień identyfikowany przez klucz, który jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> nazwą strumienia. Środowisko wywołuje następnie z powrotem pakiet VSPackage, aby odczytać ten konkretny strumień, przekazując nazwę strumienia i `IStream` wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metody.

 W tym momencie jest wykonane kolejne wywołanie do , aby sprawdzić, czy istnieje inna sekcja pliku `LoadUserOptions` .suo, która musi zostać odczytana. Ten proces jest kontynuowany, dopóki wszystkie strumienie danych w pliku .suo nie zostały odczytane i przetworzone przez środowisko.

 Po zapisaniu lub zamknięciu rozwiązania środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> metodę ze wskaźnikiem do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metody. Element zawierający informacje binarne do zapisania jest przekazywany do metody , która następnie zapisuje informacje w pliku suo i ponownie wywołuje metodę , aby sprawdzić, czy istnieje inny strumień informacji do zapisania w pliku `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> `SaveUserOptions` suo.

 Te dwie metody, i , są wywoływane rekursywnie dla każdego strumienia informacji do zapisania w pliku `SaveUserOptions` `WriteUserOptions` .suo, przekazując wskaźnik do `IVsSolutionPersistence` . Są one wywoływane rekursywnie, aby umożliwić zapisywanie wielu strumieni w pliku suo. W ten sposób informacje o użytkowniku są utrwalane wraz z rozwiązaniem i gwarantuje się, że będą dostępne przy następnym otwarciu rozwiązania.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Rozwiązania](../../extensibility/internals/solutions-overview.md)
