---
title: Opcje użytkownika rozwiązania (. Plik suo) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51833f22a445916d9b76955893e4ff5c567cf4f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948949"
---
# <a name="solution-user-options-suo-file"></a>Plik opcji użytkownika rozwiązania (Suo)
Plik opcji (suo) użytkownika rozwiązania zawiera opcje rozwiązania dla poszczególnych użytkowników. Nie można zaewidencjonować ten plik do kontroli kodu źródłowego.  
  
 Plik opcji (suo) użytkownika rozwiązania jest strukturalny magazyn lub złożone, plików przechowywanych w formacie binarnym. O nazwie strumienia jest klucz, który będzie używany do identyfikowania informacji w pliku .suo zapisywania informacji o użytkowniku do strumieni. Plik opcji użytkownika rozwiązania jest używany do przechowywania ustawień preferencji użytkownika i jest tworzony automatycznie, gdy program Visual Studio zapisuje rozwiązania.  
  
 Po otwarciu pliku .suo środowiska wylicza wszystkie aktualnie załadowanych pakietów VSPackage. Jeśli zaimplementowano pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfejsu, a następnie wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> metody na VSPackage prosisz go, aby załadować wszystkie swoje dane z pliku .suo.  
  
 Jest to napisać odpowiedzialność VSPackage wiedzieć, jakie przesyła strumieniowo do pliku .suo. Dla każdego strumienia, który zapisał pakietu VSPackage wywołuje do środowiska za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> można załadować określonego strumienia, który jest identyfikowany przez klucz, który nazywa się strumienia. Środowisko wywołuje powrót do pakietu VSPackage można odczytać określonego strumieniu przekazanie nazwy strumienia i `IStream` wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metody.  
  
 W tym momencie innego następuje wywołanie `LoadUserOptions` aby zobaczyć, czy innej sekcji pliku .suo, który ma być odczytywane. Ten proces jest kontynuowany, dopóki wszystkie strumienie danych w pliku .suo Odczyt i przetworzone przez środowisko.  
  
 Gdy rozwiązanie jest zapisywany lub zamknięte, wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> metoda ze wskaźnikiem do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metody. `IStream` Zawierający dane binarne do zapisania jest przekazywany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> metody, która następnie zapisuje te informacje w pliku .suo i wywołania `SaveUserOptions` metoda ponownie, aby sprawdzić, czy jest inny strumień informacji do zapisu .suo plik.  
  
 Te dwie metody `SaveUserOptions` i `WriteUserOptions`, są nazywane rekursywnie dla każdego strumienia danych można zapisać do pliku .suo, przekazując wskaźnik do `IVsSolutionPersistence`. Są one nazywane cyklicznie, aby umożliwić pisanie wiele strumieni w pliku .suo. W ten sposób informacje o użytkowniku utrwalone w rozwiązaniu i musi być tam przy następnym otwarciu rozwiązania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Rozwiązania](../../extensibility/internals/solutions.md)