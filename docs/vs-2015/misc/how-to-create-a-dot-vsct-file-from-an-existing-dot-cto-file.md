---
title: 'Instrukcje: Tworzenie. Plik vsct z istniejącego. Plik dyrektor ds | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: 83608d768940158dcdab427a557577677e56f7c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822441"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Instrukcje: Tworzenie. Plik vsct z istniejącego. Plik dyrektor ds
Można utworzyć plik vsct oparty na języku XML z istniejącego pliku binarnego. Dyrektor ds. Dzięki temu można korzystać z nowego formatu kompilatora tabeli poleceń. Ten proces działa nawet wtedy, gdy plik. Dyrektor ds został skompilowany z pliku CTC. Plik. vsct można edytować i skompilować w innym pliku. Dyrektor ds.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Aby utworzyć plik. vsct z pliku. Dyrektor ds  
  
1. Uzyskaj kopie pliku. Dyrektor ds i odpowiadający mu plik. CTSYM.  
  
2. Umieść pliki w tym samym katalogu co kompilator vsct.exe.  
  
3. W wierszu polecenia programu Visual Studio przejdź do katalogu, który zawiera pliki. Dyrektor ds i. CTSYM.  
  
4. Wpisz **vsct.exe** _ctofilename_**. Dyrektor ds** _vsctfilename_**. vsct-S**_symfilename_**. CTSYM**.  
  
     `ctofilename` jest nazwą pliku dyrektor ds, `vsctfilename` jest nazwą pliku vsct, który ma zostać utworzony, a `symfilename` to nazwa pliku. CTSYM.  
  
     Ten proces powoduje utworzenie nowego pliku kompilatora tabeli poleceń XML vsct. Plik można edytować i skompilować przy użyciu vsct.exe, kompilatora vsct, tak jak każdy inny plik. vsct.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie. Plik vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)