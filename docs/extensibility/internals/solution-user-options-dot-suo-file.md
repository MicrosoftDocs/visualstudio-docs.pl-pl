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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723812"
---
# <a name="solution-user-options-suo-file"></a>Plik opcji użytkownika rozwiązania (Suo)
Plik Opcje użytkownika rozwiązania (. suo) zawiera opcje rozwiązania dla poszczególnych użytkowników. Ten plik nie powinien być zaewidencjonowany w kontroli kodu źródłowego.

 Plik opcji użytkownika rozwiązania (. suo) jest magazynem strukturalnym lub złożonym, plik jest przechowywany w formacie binarnym. Informacje o użytkowniku są zapisywane w strumieniach o nazwie klucza, który będzie używany do identyfikowania informacji w pliku. suo. Plik opcji użytkownika rozwiązania służy do przechowywania ustawień preferencji użytkownika i jest tworzony automatycznie, gdy program Visual Studio zapisuje rozwiązanie.

 Gdy środowisko otwiera plik. suo, wylicza wszystkie aktualnie załadowane pakietów VSPackage. Jeśli pakietu VSPackage implementuje interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>, środowisko wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> na pakietu VSPackage z prośbą o załadowanie wszystkich danych z pliku. suo.

 Jest on odpowiedzialny za pakietu VSPackage, aby wiedzieć, jakie strumienie mogą być zapisywane w pliku. suo. Dla każdego zapisanego strumienia pakietu VSPackage wywołuje z powrotem do środowiska za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> w celu załadowania określonego strumienia, który jest identyfikowany przez klucz, który jest nazwą strumienia. Środowisko następnie wywołuje z powrotem do pakietu VSPackage, aby odczytać ten konkretny strumień, przekazując nazwę strumienia i wskaźnik `IStream` do metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>.

 W tym momencie inne wywołanie `LoadUserOptions`, aby sprawdzić, czy istnieje inna sekcja pliku SUO, która musi zostać odczytana. Ten proces jest kontynuowany do momentu odczytania i przetworzenia przez środowisko wszystkich strumieni danych w pliku. suo.

 Gdy rozwiązanie zostanie zapisane lub zamknięte, środowisko wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> ze wskaźnikiem do metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>. @No__t_0 zawierający informacje binarne do zapisania są przesyłane do metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>, która następnie zapisuje informacje w pliku. suo i ponownie wywołuje metodę `SaveUserOptions`, aby sprawdzić, czy istnieje inny strumień informacji do zapisu w pliku SUO.

 Te dwie metody, `SaveUserOptions` i `WriteUserOptions`, są nazywane cyklicznie dla każdego strumienia informacji, które mają zostać zapisane w pliku. suo, przekazując wskaźnik do `IVsSolutionPersistence`. Są one nazywane cyklicznie, aby umożliwić zapisanie wielu strumieni do pliku. suo. W ten sposób informacje o użytkowniku są utrwalane w rozwiązaniu i zagwarantowane będzie przy następnym otwarciu rozwiązania.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Rozwiązania](../../extensibility/internals/solutions-overview.md)