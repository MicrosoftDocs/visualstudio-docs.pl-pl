---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89326676"
---
W tych krokach przedstawiono tylko podstawową konfigurację usług IIS. Aby uzyskać bardziej szczegółowe informacje lub zainstalować program na komputerze stacjonarnym z systemem Windows, zobacz [Publikowanie w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) lub [IIS 8,0 przy użyciu ASP.NET 3,5 i ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

W przypadku systemów operacyjnych Windows Server Użyj kreatora **dodawania ról i funkcji** za pośrednictwem linku **Zarządzaj** łączem lub **pulpitu nawigacyjnego** w **Menedżer serwera**. W kroku **role serwera** zaznacz pole wyboru **serwer sieci Web (IIS)**.

![W kroku wybierz role serwera zostanie wybrana rola IIS serwera sieci Web.](../media/remotedbg-server-roles-ws2012.png)

W kroku **usługi ról** wybierz żądane usługi roli IIS lub zaakceptuj domyślne usługi ról. Jeśli chcesz włączyć wdrażanie za pomocą ustawień publikowania i Web Deploy upewnij się, że są zaznaczone **skrypty i narzędzia zarządzania usługami IIS** .

Wykonaj kroki potwierdzeń, aby zainstalować rolę i usługi serwera sieci Web. Serwer/ponowne uruchomienie usług IIS nie jest wymagane po zainstalowaniu roli Serwer sieci Web (IIS).