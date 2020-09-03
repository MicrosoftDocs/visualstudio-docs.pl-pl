---
title: Debugowanie wdrożonych aplikacji ASP.NET | Microsoft Docs
ms.date: 06/30/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 8d787e6586a9dcce2ca4d2c840f67e652bfc5714
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350553"
---
# <a name="debugging-deployed-aspnet-applications"></a>Debugowanie wdrożonych aplikacji ASP.NET
Aby użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do debugowania wdrożonej aplikacji, należy dołączyć do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego i upewnić się, że debuger ma dostęp do symboli dla aplikacji. Należy również odszukać i otworzyć pliki źródłowe aplikacji. Aby uzyskać więcej informacji, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [instrukcje: znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)i [wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Jeśli dołączysz do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego w celu debugowania i trafisz punkt przerwania, cały kod zarządzany w procesie roboczym zostanie zatrzymany. Zatrzymanie całego kodu zarządzanego w procesie roboczym może spowodować zatrzymanie pracy dla wszystkich użytkowników na serwerze. Przed rozpoczęciem debugowania na serwerze produkcyjnym należy wziąć pod uwagę potencjalny wpływ na pracę produkcyjną.

Proces dołączania do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego jest taki sam jak dołączanie do innych procesów zdalnych. Po dołączeniu, jeśli nie masz poprawnego otwartego projektu, pojawi się okno dialogowe, gdy aplikacja zostanie przerwana. To okno dialogowe pyta o lokalizację plików źródłowych aplikacji. Nazwa pliku określona w oknie dialogowym musi być zgodna z nazwą pliku określoną w symbolach debugowania na serwerze sieci Web. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Aby skonfigurować zdalne debugowanie w usługach IIS, zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Wiele [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web odwołuje się do bibliotek DLL, które zawierają logikę biznesową lub inny kod użyteczny. Takie odwołanie powoduje skopiowanie biblioteki DLL z komputera lokalnego do folderu \Bin katalogu wirtualnego aplikacji sieci Web podczas wdrażania aplikacji. Podczas debugowania należy pamiętać, że aplikacja sieci Web odwołuje się do tej kopii biblioteki DLL, a nie kopii na komputerze lokalnym.

## <a name="see-also"></a>Zobacz też
- [Debuguj aplikacje ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Porady: włączanie debugowania dla aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Instrukcje: Znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)