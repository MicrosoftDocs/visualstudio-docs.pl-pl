---
title: Opcje użytkownika rozwiązania (. Suo) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705315"
---
# <a name="solution-user-options-suo-file"></a>Plik opcji użytkownika rozwiązania (Suo)
Plik Opcje użytkownika rozwiązania (. suo) zawiera opcje rozwiązania dla poszczególnych użytkowników. Ten plik nie powinien być zaewidencjonowany w kontroli kodu źródłowego.

 Plik opcji użytkownika rozwiązania (. suo) jest magazynem strukturalnym lub złożonym, plik jest przechowywany w formacie binarnym. Informacje o użytkowniku są zapisywane w strumieniach o nazwie klucza, który będzie używany do identyfikowania informacji w pliku. suo. Plik opcji użytkownika rozwiązania służy do przechowywania ustawień preferencji użytkownika i jest tworzony automatycznie, gdy program Visual Studio zapisuje rozwiązanie.

 Gdy środowisko otwiera plik. suo, wylicza wszystkie aktualnie załadowane pakietów VSPackage. Jeśli pakietu VSPackage implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfejs, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> metodę z pakietu VSPackage z prośbą o załadowanie wszystkich danych z pliku. suo.

 Jest on odpowiedzialny za pakietu VSPackage, aby wiedzieć, jakie strumienie mogą być zapisywane w pliku. suo. Dla każdego zapisanego strumienia, pakietu VSPackage wywołuje z powrotem do środowiska za pomocą programu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> Aby załadować konkretny strumień identyfikowany przez klucz, który jest nazwą strumienia. Środowisko następnie wywołuje z powrotem do pakietu VSPackage, aby odczytywać ten konkretny strumień, przekazując nazwę strumienia i `IStream` wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metody.

 W tym momencie inne wywołanie w `LoadUserOptions` celu sprawdzenia, czy istnieje inna sekcja pliku. suo, która musi zostać odczytana. Ten proces jest kontynuowany do momentu odczytania i przetworzenia przez środowisko wszystkich strumieni danych w pliku. suo.

 Gdy rozwiązanie zostanie zapisane lub zamknięte, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> metodę ze wskaźnikiem do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metody. `IStream`Zawierające informacje binarne do zapisania są przesyłane do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> metody, która następnie zapisuje informacje w pliku. suo i `SaveUserOptions` ponownie wywołuje metodę, aby sprawdzić, czy istnieje inny strumień informacji do zapisu w pliku. suo.

 Te dwie metody `SaveUserOptions` i `WriteUserOptions` , są nazywane rekursywnie dla każdego strumienia informacji, które mają być zapisane w pliku. suo, przekazując wskaźnik do `IVsSolutionPersistence` . Są one nazywane cyklicznie, aby umożliwić zapisanie wielu strumieni do pliku. suo. W ten sposób informacje o użytkowniku są utrwalane w rozwiązaniu i zagwarantowane będzie przy następnym otwarciu rozwiązania.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Rozwiązania](../../extensibility/internals/solutions-overview.md)
