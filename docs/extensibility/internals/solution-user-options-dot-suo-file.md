---
title: Opcje użytkownika rozwiązania (. Suo) Plik | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705315"
---
# <a name="solution-user-options-suo-file"></a>Plik opcji użytkownika rozwiązania (Suo)
Plik opcji użytkownika rozwiązania (.suo) zawiera opcje rozwiązania dla użytkownika. Ten plik nie powinien być zaewidencjonowany do kontroli kodu źródłowego.

 Plik opcji użytkownika rozwiązania (.suo) jest magazynem strukturalnym lub złożonym plikiem przechowywanym w formacie binarnym. Informacje o użytkowniku można zapisać w strumieniach, przy czym nazwa strumienia jest kluczem, który będzie używany do identyfikowania informacji w pliku .suo. Plik opcji użytkownika rozwiązania jest używany do przechowywania ustawień preferencji użytkownika i jest tworzony automatycznie, gdy program Visual Studio zapisuje rozwiązanie.

 Gdy środowisko otwiera plik .suo, wylicza wszystkie aktualnie ładowane pakiety VSPackages. Jeśli VSPackage implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfejs, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> środowisko wywołuje metodę na VSPackage z prośbą, aby załadować wszystkie swoje dane z pliku .suo.

 Jest to odpowiedzialność VSPackage wiedzieć, jakie strumienie może mieć zapisane w pliku .suo. Dla każdego strumienia, który napisał, VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> wywołuje z powrotem do środowiska, aby załadować określonego strumienia, który jest identyfikowany przez klucz, który jest nazwą strumienia. Środowisko następnie wywołuje z powrotem do VSPackage odczytać tego określonego `IStream` strumienia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> przekazywania nazwy strumienia i wskaźnik do metody.

 W tym momencie zostanie `LoadUserOptions` wykonane inne wywołanie, aby sprawdzić, czy istnieje inna sekcja pliku .suo, która musi zostać odczytana. Ten proces jest kontynuowany do momentu, gdy wszystkie strumienie danych w pliku .suo zostały odczytane i przetworzone przez środowisko.

 Gdy rozwiązanie jest zapisywane lub zamknięte, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metodę za pomocą wskaźnika do metody. Zawierające `IStream` informacje binarne, które mają <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> być zapisane jest przekazywana do metody, która następnie `SaveUserOptions` zapisuje informacje do pliku .suo i wywołuje metodę ponownie, aby sprawdzić, czy istnieje inny strumień informacji do zapisu do pliku .suo.

 Te dwie `SaveUserOptions` metody `WriteUserOptions`i , są nazywane rekursywnie dla każdego strumienia informacji, które `IVsSolutionPersistence`mają być zapisane w pliku .suo, przechodząc w wskaźniku do . Są one nazywane rekursywnie, aby umożliwić zapisywanie wielu strumieni do pliku .suo. W ten sposób informacje o użytkowniku są zachowywane z rozwiązaniem i jest gwarantowane, aby być tam następnym razem, gdy rozwiązanie jest otwierane.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Rozwiązania](../../extensibility/internals/solutions-overview.md)
