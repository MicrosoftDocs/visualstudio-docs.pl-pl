---
title: 'Instrukcje: Tworzenie. Plik Vsct z istniejącej. Plik CTC | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 2d5ba5a271cd7132d9750fc0569b801022aeb932
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117859"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Instrukcje: Tworzenie. Plik Vsct z istniejącej. Plik CTC
Można utworzyć pliku vsct oparty na składni XML z istniejącego pliku źródłowego .ctc tabeli poleceń. Dzięki temu możesz korzystać z zalet nowego opartego na języku XML [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] format kompilatora tabeli (VSCT) polecenia.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Do utworzenia pliku vsct z pliku .ctc  
  
1. Uzyskaj kopię programu języka Perl.  
  
2. Uzyskaj kopię skryptu Perl ConvertCTCToVSCT.pl, zazwyczaj znajduje się w  *\<ścieżka instalacji programu Visual Studio SDK >* \VisualStudioIntegration\Tools\bin folderu.  
  
3. Uzyskaj kopię pliku źródłowego .ctc, który ma zostać przekonwertowany.  
  
4. Umieść pliki w tym samym katalogu.  
  
5. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] polecenia monitu okna, przejdź do katalogu.  
  
6. Typ  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     gdzie PkgCmd.ctc jest nazwą pliku .ctc a PkgCmd.vsct jest nazwą pliku vsct, który chcesz utworzyć.  
  
     Spowoduje to utworzenie nowego vsct polecenia tabeli źródłowego pliku XML. Plik można kompilować przy użyciu Vsct.exe, kompilator VSCT, tak jak dowolnego innego pliku vsct.  
  
    > [!NOTE]
    >  Można zwiększyć czytelność pliku vsct przez ponowne formatowanie komentarze XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie. Pliku Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)