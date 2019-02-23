---
title: Debugowanie aplikacji ASP.NET wdrożonej | Dokumentacja firmy Microsoft
ms.date: 06/30/2017
ms.topic: conceptual
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
ms.openlocfilehash: bfbf5dc7421446c863bfd104f4247bb06411dfb2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717627"
---
# <a name="debugging-deployed-aspnet-applications"></a>Debugowanie ASP.NET wdrożonej aplikacji
Aby użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugowanie wdrożonej aplikacji, należy dołączyć do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego przetwarzania i upewnij się, że debuger ma dostęp do symboli dla aplikacji. Należy również zlokalizować i Otwórz pliki źródłowe dla aplikacji. Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [jak: Znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), i [wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Jeśli dołączysz do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego do debugowania i trafiony punkt przerwania, wszystkie zarządzane kodu w zatrzymanie procesu roboczego. Zatrzymywanie zarządzanego kodu w procesie roboczym, może spowodować przerwy w pracy dla wszystkich użytkowników na serwerze. Przed debugowania na serwerze produkcyjnym, należy wziąć pod uwagę potencjalny wpływ na pracy w środowisku produkcyjnym.

Dołączanie do procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego jest taki sam jak dołączanie do zdalnego procesu. Gdy użytkownik jest podłączony, jeśli nie masz odpowiedni projekt, Otwórz, pojawi się okno dialogowe, gdy aplikacja zostanie przerwany. To okno dialogowe poprosi o podanie lokalizacji plików źródłowych dla aplikacji. Nazwa pliku, który określisz w oknie dialogowym musi odpowiadać nazwa pliku określona w symbole debugowania na serwerze sieci Web. Aby uzyskać więcej informacji, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Aby skonfigurować zdalne debugowanie w programie IIS, zobacz [zdalnego debugowania ASP.NET, na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
>  Wiele [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bibliotek DLL, które zawierają logikę biznesową lub inny kod przydatne odwoływać się do aplikacji sieci Web. Odniesienie kopiuje biblioteki DLL z komputera lokalnego, do folderu \bin katalog wirtualny dla aplikacji sieci Web, gdy aplikacja jest wdrażana. Podczas debugowania, należy pamiętać, że aplikacja sieci Web odwołuje się do tej kopii biblioteki dll, a nie kopię na komputerze lokalnym.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Instrukcje: Włączanie debugowania dla aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Instrukcje: Znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)