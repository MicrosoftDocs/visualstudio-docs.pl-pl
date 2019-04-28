---
title: Debugowanie wdrożonych aplikacji sieci Web | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444075"
---
# <a name="debugging-deployed-web-applications"></a>Debugowanie wdrożonych aplikacji internetowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli potrzebujesz debugować aplikację sieci Web, która jest uruchomiona na serwerze produkcyjnym, powinna być podejmowana z rozwagą. Jeśli dołączysz do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego proces debugowania i Traf punkt przerwania, na przykład, wszystkie zarządzane kodu w zatrzymanie procesu roboczego. Zatrzymywanie zarządzanego kodu w procesie roboczym, może spowodować przerwy w pracy dla wszystkich użytkowników na serwerze. Przed debugowania na serwerze produkcyjnym, należy wziąć pod uwagę potencjalny wpływ na pracy w środowisku produkcyjnym.  
  
 Aby użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugowanie wdrożonej aplikacji, należy dołączyć do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego przetwarzania i upewnij się, że debuger ma dostęp do symboli dla aplikacji. Należy również zlokalizować i Otwórz pliki źródłowe dla aplikacji. Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [jak: Znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), i [wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
> Wiele [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] bibliotek DLL, które zawierają logikę biznesową lub inny kod przydatne odwoływać się do aplikacji sieci Web. Odniesienie automatycznie kopiuje bibliotekę DLL z komputera lokalnego do folderu \bin katalog wirtualny dla aplikacji sieci Web. Podczas debugowania, należy pamiętać, że aplikacja sieci Web odwołuje się do tej kopii biblioteki dll, a nie kopię na komputerze lokalnym.  
  
 Dołączanie do procesu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego jest taki sam jak dołączanie do zdalnego procesu. Gdy użytkownik jest podłączony, jeśli nie masz odpowiedni projekt, Otwórz, pojawi się okno dialogowe, gdy aplikacja zostanie przerwany. To okno dialogowe poprosi o podanie lokalizacji plików źródłowych dla aplikacji. Nazwa pliku, który określisz w oknie dialogowym musi odpowiadać nazwa pliku określona w symbole debugowania na serwerze sieci Web. Aby uzyskać więcej informacji, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Debugowanie aplikacji sieci Web i skryptu](../debugger/debugging-web-applications-and-script.md)   
 [Instrukcje: Włącz debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Instrukcje: Znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
