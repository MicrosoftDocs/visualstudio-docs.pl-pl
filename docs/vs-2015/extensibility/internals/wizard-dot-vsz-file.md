---
title: Kreator (. Vsz) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab1adde4c7018f136f47769e16a8ce2fedf72c93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687666"
---
# <a name="wizard-vsz-file"></a>Kreator (plik Vsz)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zintegrowane środowisko programistyczne (IDE) używa plików. vsz do uruchamiania kreatorów. Te pliki. vsz zawierają informacje używane przez środowisko IDE do określenia kreatora do wywołania i informacji, które należy przekazać do kreatora.  
  
 Plik. vsz jest wersją pliku tekstowego w formacie. ini, który nie zawiera żadnych sekcji. Informacje znane do IDE są przechowywane na początku pliku. Zapewnia to połączenie między kreatorem, który jest wywoływany przez środowisko IDE, i parametry, które znajdują się w pliku. vsz do przesłania do IDE. Pozostała część pliku zawiera parametry, które są specyficzne dla kreatora i które mają być zbierane przez środowisko IDE i przesyłane do określonego kreatora.  
  
 Poniższy przykład pokazuje zawartość pliku. vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Poniżej przedstawiono części w pliku. vsz.  
  
|Część|Opis|  
|----------|-----------------|  
|VSWizard|Pierwszy parametr w pliku jest numerem wersji formatu pliku szablonu. Ten numer wersji musi być 6,0, 7,0, 7,1 lub 8,0. Nie można uruchomić innych liczb i spowodować błąd nieprawidłowego formatu.|  
|Kreatora|To pole zawiera obiekt OLE ProgID kreatora lub alternatywnie reprezentacja identyfikatora GUID kreatora, który jest współtworzony przez IDE.|  
|Param|Te części są opcjonalne. W razie konieczności można dodać dowolną liczbę.|  
  
 Parametry umożliwiają plikowi. vsz przekazywanie dodatkowych parametrów niestandardowych do kreatora. Każda wartość jest przenoszona jako element String w tablicy wariantów do kreatora. Aby uzyskać więcej informacji, zobacz [parametry niestandardowe](../../extensibility/internals/custom-parameters.md). Informacje o sposobach używania pliku. vsz w programowaniu kreatorów niestandardowych znajdują się w temacie [. Plik VSZ (formant projektu)](https://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)  
  
 Aby dodać domyślny identyfikator ustawień regionalnych do pliku. vsz, określ `FALLBACK_LCID` = xxxx, gdzie xxxx jest identyfikatorem ustawień regionalnych, na przykład 1033 dla języka angielskiego. Gdy `FALLBACK_LCID` parametr jest zdefiniowany, Kreator używa podanego identyfikatora ustawień regionalnych w przypadku nieznalezienia bieżącego identyfikatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)   
 [Kreatorów](../../extensibility/internals/wizards.md)   
 [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
