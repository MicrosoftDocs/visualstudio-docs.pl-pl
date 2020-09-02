---
title: Debugowanie wdrożonych aplikacji sieci Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9608643801255d6c2cbf278cbfd96908f1f3911d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64832456"
---
# <a name="debugging-deployed-web-applications"></a>Debugowanie wdrożonych aplikacji internetowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli konieczne jest debugowanie aplikacji sieci Web działającej na serwerze produkcyjnym, należy to zrobić z ostrożnością. Jeśli dołączysz do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego w celu debugowania i trafisz punkt przerwania, na przykład cały kod zarządzany w procesie roboczym zostanie zatrzymany. Zatrzymanie całego kodu zarządzanego w procesie roboczym może spowodować zatrzymanie pracy dla wszystkich użytkowników na serwerze. Przed rozpoczęciem debugowania na serwerze produkcyjnym należy wziąć pod uwagę potencjalny wpływ na pracę produkcyjną.  
  
 Aby użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do debugowania wdrożonej aplikacji, należy dołączyć do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego i upewnić się, że debuger ma dostęp do symboli dla aplikacji. Należy również odszukać i otworzyć pliki źródłowe aplikacji. Aby uzyskać więcej informacji, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [instrukcje: znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)i [wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
> Wiele [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web odwołuje się do bibliotek DLL, które zawierają logikę biznesową lub inny kod użyteczny. Takie odwołanie powoduje automatyczne skopiowanie biblioteki DLL z komputera lokalnego do folderu \Bin katalogu wirtualnego aplikacji sieci Web. Podczas debugowania należy pamiętać, że aplikacja sieci Web odwołuje się do tej kopii biblioteki DLL, a nie kopii na komputerze lokalnym.  
  
 Proces dołączania do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego jest taki sam jak dołączanie do innych procesów zdalnych. Po dołączeniu, jeśli nie masz poprawnego otwartego projektu, pojawi się okno dialogowe, gdy aplikacja zostanie przerwana. To okno dialogowe pyta o lokalizację plików źródłowych aplikacji. Nazwa pliku określona w oknie dialogowym musi być zgodna z nazwą pliku określoną w symbolach debugowania na serwerze sieci Web. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Debugowanie aplikacji sieci Web i skryptu](../debugger/debugging-web-applications-and-script.md)   
 [Instrukcje: Włączanie debugowania dla aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Instrukcje: Znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
