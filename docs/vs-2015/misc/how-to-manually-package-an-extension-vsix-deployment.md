---
title: 'Instrukcje: ręczne pakowanie rozszerzenia (wdrożenie VSIX) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: a615aea75ec00e49ee4d2837b8b4e2b1d20d3306
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293617"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Instrukcje: ręczne pakowanie rozszerzenia (wdrożenie VSIX)
Można utworzyć pakiet VSIX, aby obsłużyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenie do wdrożenia. Istnieją trzy sposoby tworzenia pakietu:  
  
- Utwórz projekt pakietu VSIX przy użyciu jednego z szablonów rozszerzalności, które znajdują się w zestawie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK. Jest to najprostsza opcja dla większości scenariuszy.  
  
- Zawiń dane wyjściowe projektu rozszerzenia w pustym [projekcie VSIX](../extensibility/vsix-project-template.md). Zalecamy korzystanie z tej opcji w przypadku szablonów, nieobsługiwanych zestawów i typów niestandardowych.  
  
- Utwórz ręcznie pakiet VSIX. Zalecamy tę opcję tylko wtedy, gdy inne dwie opcje są niedostępne.  
  
  W tym dokumencie opisano trzecią opcję.  
  
## <a name="creating-a-vsix-package"></a>Tworzenie pakietu VSIX  
 Aby ręcznie spakować rozszerzenie, Dodaj plik manifestu rozszerzenia i [Content_Types]. XML do projektu rozszerzenia, umieść je w skompresowanym pliku razem z danymi wyjściowymi kompilacji i Zmień nazwę pliku skompresowanego tak, aby miał rozszerzenie nazwy pliku. VSIX. Rozszerzenie do spakowania musi być typu, który jest obsługiwany przez [schemat VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
> Nazwy plików w pakietach VSIX nie mogą zawierać spacji ani znaków, które są zarezerwowane w Uniform Resource Identifier (URI), zgodnie z definicją w obszarze [\[RFC2396\]](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Aby ręcznie utworzyć pakiet VSIX  
  
1. Utwórz rozszerzenie Visual Studio typu, który jest obsługiwany przez schemat VSIX.  
  
2. Utwórz plik XML i nadaj mu nazwę `extension.vsixmanifest`.  
  
3. Wypełnij plik Extension. vsixmanifest zgodnie ze schematem VSIX. Przykładowy manifest można znaleźć w temacie [PackageManifest element (root element, VSX Schema)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4. Utwórz drugi plik XML i nadaj mu nazwę `[Content_Types].xml`.  
  
5. Wypełnij plik [Content_Types]. XML, jak określono w [strukturze pliku Content_types\]. XML](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6. Umieść pliki XML w katalogu wraz z rozszerzeniem, które ma zostać wdrożone.  
  
     W przypadku szablonu projektu lub szablonu elementu Umieść plik zip zawierający szablon w tym samym folderze, w którym znajdują się pliki XML. Nie umieszczaj plików XML w pliku zip.  
  
     We wszystkich innych przypadkach pliki XML należy umieścić w tym samym katalogu, co w danych wyjściowych kompilacji.  
  
7. W Eksploratorze Windows kliknij prawym przyciskiem myszy folder zawierający zawartość rozszerzenia i dwa pliki XML, kliknij polecenie **Wyślij do**, a następnie kliknij **folder skompresowany (zip)** .  
  
8. Zmień nazwę otrzymanego pliku zip na *filename*. vsix, gdzie *filename* to nazwa pliku redystrybucyjnego, który instaluje pakiet.  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłka rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [PackageManifest — element (element główny, schemat VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)