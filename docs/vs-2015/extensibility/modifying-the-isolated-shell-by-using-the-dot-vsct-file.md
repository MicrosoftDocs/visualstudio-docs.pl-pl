---
title: Modyfikowanie izolowanej powłoki przy użyciu. Plik vsct | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194234"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modyfikowanie programu Isolated Shell przy użyciu pliku Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekt interfejsu użytkownika dla projektu powłoki izolowanej programu Visual Studio zawiera plik. vsct, który umożliwia określenie, które grupy aplikacji i poszczególne polecenia są dostępne w aplikacji. Poniżej znajduje się fragment niezmodyfikowanego pliku. vsct.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Domyślnie większość poleceń i grup poleceń jest uwzględniona. Aby wykluczyć polecenie lub grupę poleceń, po prostu Usuń komentarz z tego polecenia lub grupy.  
  
 Aby na przykład usunąć kolejne polecenia i poprzednie okienka, Usuń komentarz z `No_PaneNextPaneCommand` i `No_PanePrevPaneCommand` wpisów:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Aby zapoznać się z bardziej szczegółowym przykładem, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Pliki, do których istnieją odwołania  
 Plik default. vsct aplikacji odwołuje się do poniższych plików. Te pliki znajdują się w podkatalogu \VisualStudioIntegration\Common\Inc\ w katalogu instalacyjnym zestawu SDK programu Visual Studio.  
  
|Plik|Opis|  
|----------|-----------------|  
|wbids. h|Tożsamości interfejsu użytkownika dla pakietu przeglądania sieci Web.|  
|AppIDCmdUsed. vsct|Tabela poleceń dla podstawowych elementów interfejsu użytkownika programu Visual Studio.|  
|EmulatorCmdUsed. vsct|Tabela poleceń dla Emacs: i krótkiego edytora edytorów elementów interfejsu użytkownika.|  
|Vsdebugguids. h|Definiuje identyfikatory GUID poleceń, strony opcji i innych funkcji debugera programu Visual Studio.|  
|VsDbgCmdUsed. vsct|Tabela poleceń dla debugera.|  
  
 Plik AppIDCmdUsed. vsct zawiera elementy interfejsu użytkownika programu Visual Studio na podstawie symboli zdefiniowanych w pliku Application. vsct.  
  
 Aby uzyskać więcej informacji, zobacz [Projektowanie tabeli poleceń XML (. Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) i [Dokumentacja schematu XML vsct](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Shell (izolowany)](../extensibility/visual-studio-isolated-shell.md)
