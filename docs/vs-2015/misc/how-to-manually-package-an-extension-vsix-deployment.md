---
title: 'Instrukcje: Ręcznie pakietu rozszerzenia (VSIX wdrożenie) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: 81bf6c5ef975d7ce154c1d8bb987e962dfdf4ec2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040744"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Instrukcje: Ręcznie pakietu rozszerzenia (VSIX wdrożenia)
Możesz utworzyć pakiet VSIX do opakowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzeń dla wdrożenia. Istnieją trzy sposoby, aby utworzyć pakiet:  
  
- Utwórz projekt VSIX pakietu przy użyciu jednego z szablonów rozszerzeń, które są zawarte w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawu SDK. Jest to opcja najłatwiejsza, w przypadku większości scenariuszy.  
  
- Zawijanie dane wyjściowe projektu rozszerzenia w pustą [projekt VSIX](../extensibility/vsix-project-template.md). Zaleca się tej opcji dla szablonów, nieobsługiwanych zestawów i typów niestandardowych.  
  
- Ręcznie utworzyć pakiet VSIX. Zaleca się tej opcji tylko wtedy, gdy nie są dostępne dwie opcje.  
  
  W tym dokumencie opisano trzecią opcję.  
  
## <a name="creating-a-vsix-package"></a>Tworzenie pakietu VSIX  
 Aby ręcznie pakiet rozszerzenia, Dodaj plik extension.manifest i pliku [Content_Types] .xml do projektu rozszerzenia, umieść je w pliku skompresowanym wraz z danych wyjściowych kompilacji, a tak, że ma rozszerzenie nazwy pliku .vsix, Zmień nazwę skompresowanego pliku. Rozszerzenie do umieszczenia w pakiecie musi być typu, który jest obsługiwany przez [schematu VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
>  Nazwy plików pakietów VSIX nie może zawierać spacji ani znaków, które są zastrzeżone w identyfikatorach URI (Uniform Resource), zdefiniowane w obszarze [ \[specyfikacja RFC 2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Aby ręcznie utworzyć pakiet VSIX  
  
1. Tworzenie rozszerzenia programu Visual Studio, typu, który jest obsługiwany przez schemat VSIX.  
  
2. Utwórz plik XML i nadaj mu nazwę `extension.vsixmanifest`.  
  
3. Wprowadź w pliku extension.vsixmanifest zgodnie ze schematem VSIX. Manifest przykładzie można zobaczyć [PackageManifest elementu (Element główny, schemat VSX)](http://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4. Utwórz drugi plik XML i nadaj mu nazwę `[Content_Types].xml`.  
  
5. Wypełnij pliku [Content_Types] .xml, jak to określono w [struktury Content_types\]XML pliku](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6. Oba pliki XML należy umieścić w katalogu wraz z rozszerzenia, które mają zostać wdrożone.  
  
     W przypadku szablonu projektu lub szablon elementu umieść plik zip zawierający szablon, w tym samym folderze co pliki XML. Nie należy umieszczać pliki XML w pliku .zip.  
  
     We wszystkich innych przypadkach należy umieścić pliki XML w tym samym katalogu co dane wyjściowe kompilacji.  
  
7. W Eksploratorze Windows, kliknij prawym przyciskiem myszy folder, który zawiera rozszerzenie zawartości oraz dwóch plikach XML, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)**.  
  
8. Zmień nazwę wynikowy plik zip *Filename*.vsix, gdzie *Filename* to nazwa pliku pakietu redystrybucyjnego, który instaluje pakiet.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia programu Visual Studio wysyłki](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Element PackageManifest (Element główny, VSX schematu)](http://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)