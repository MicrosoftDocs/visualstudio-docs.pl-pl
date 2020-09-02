---
title: 'Instrukcje: Tworzenie. Plik vsct z istniejącego. Plik CTC | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 7b963436e9d968dd5ba3829e97d0fd0c52e49641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796914"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Instrukcje: Tworzenie. Plik vsct z istniejącego. Plik CTC
Można utworzyć plik. vsct opartego na języku XML z istniejącej tabeli poleceń. CTC plik źródłowy. Dzięki temu można skorzystać z nowego formatu kompilatora tabeli poleceń opartych na języku XML [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (vsct).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Aby utworzyć plik. vsct z pliku. CTC  
  
1. Uzyskaj kopię języka Perl.  
  
2. Uzyskaj kopię skryptu języka Perl ConvertCTCToVSCT.pl, zazwyczaj znajdującą się w *\<Visual Studio SDK installation path>* folderze \VisualStudioIntegration\Tools\bin.  
  
3. Uzyskaj kopię pliku źródłowego. CTC, który chcesz skonwertować.  
  
4. Umieść pliki w tym samym katalogu.  
  
5. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknie wiersza polecenia przejdź do katalogu.  
  
6. Typ  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     gdzie PkgCmd. CTC jest nazwą pliku. ctc i PkgCmd. vsct to nazwa pliku. vsct, który ma zostać utworzony.  
  
     Spowoduje to utworzenie nowego pliku źródłowego tabeli poleceń XML vsct. Plik można skompilować przy użyciu Vsct.exe, kompilatora VSCT, tak jak każdy inny plik. vsct.  
  
    > [!NOTE]
    > Można zwiększyć czytelność pliku. vsct przez ponowne sformatowanie komentarzy XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie. Plik vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)