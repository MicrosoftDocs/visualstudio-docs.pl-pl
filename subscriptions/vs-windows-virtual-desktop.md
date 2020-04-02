---
title: Korzyści pulpitu wirtualnego systemu Microsoft Windows w subskrypcjach programu Visual Studio | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/01/2020
ms.topic: conceptual
description: Dowiedz się, jak korzystać z pulpitu wirtualnego systemu Microsoft Windows za pośrednictwem subskrypcji programu Visual Studio
ms.openlocfilehash: 3954a3e86c319b8d433e509a8b283201c3313410
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80550694"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Dostęp do pulpitu wirtualnego systemu Windows w subskrypcjach 
Subskrybenci programu Visual Studio mogą teraz korzystać z poszczególnych kredytów platformy Azure dla usług pulpitu wirtualnego systemu Microsoft Windows.  
Windows Virtual Desktop to kompleksowa usługa wirtualizacji pulpitu i aplikacji działająca w chmurze. Jest to jedyna infrastruktura pulpitu wirtualnego (VDI), która zapewnia uproszczone zarządzanie, wielosesyjne systemy Windows 10, optymalizacje dla usługi Office 365 ProPlus i obsługę środowisk usług pulpitu zdalnego (RDS). Wdrażaj i skaluj swoje pulpity i aplikacje systemu Windows na platformie Azure w ciągu kilku minut i uzyskaj wbudowane funkcje zabezpieczeń i zgodności.
Oto, co możesz zrobić po uruchomieniu pulpitu wirtualnego systemu Windows na platformie Azure:
- Konfigurowanie wielosesyjnego wdrożenia systemu Windows 10, które zapewnia pełny system Windows 10 ze skalowalnością
- Zwirtualizuj office 365 ProPlus i optymalizuj ją tak, aby działała w wirtualnych scenariuszach dla wielu użytkowników
- Zapewnienie pulpitom wirtualnym systemu Windows 7 bezpłatnych rozszerzonych aktualizacji zabezpieczeń
- Przenieś istniejące usługi pulpitu zdalnego (RDS) oraz pulpity i aplikacje systemu Windows Server na dowolnym komputerze
- Wirtualizuj zarówno pulpity, jak i aplikacje
- Zarządzanie pulpitami i aplikacjami dla systemów Windows 10, Windows Server i Windows 7 dzięki ujednoliconym środowisku zarządzania Aby uzyskać więcej informacji na temat tego, co można zrobić z pulpitem wirtualnym systemu Windows, obejrzyj [film wprowadzający](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Korzystanie z pulpitu wirtualnego systemu Windows z platformą Azure 
Subskrybenci programu Visual Studio mają teraz kilka sposobów korzystania z subskrypcji platformy Azure w celu płacenia za usługi pulpitu wirtualnego systemu Windows:
- [Poszczególne kredyty usługi Azure DevTest](vs-azure.md).  Subskrybenci, którzy otrzymują pojedyncze kredyty usługi Azure DevTest w ramach swoich subskrypcji, mogą używać tych kredytów do płacenia za usługi pulpitu wirtualnego systemu Windows.  Wysokość miesięcznego kredytu zależy od poziomu subskrypcji.
- [Subskrypcje usługi Azure DevTest Pay-as-you-Go](vs-azure-payg.md).  Możesz utworzyć subskrypcje platformy Azure i dołączyć instrument płatniczy, aby mieć bezproblemowy sposób płacenia za korzystanie z pulpitu wirtualnego systemu Windows. 
- [Oferta DevTest umowy azure enterprise agreement](azure-ea-devtest.md).  Dzięki tej ofercie subskrybenci z umowami Enterprise Agreement mogą płacić za pulpit wirtualny systemu Windows z platformą Azure po obniżonych cenach. 

## <a name="requirements"></a>Wymagania
Pulpit wirtualny systemu Windows wymaga usługi Azure Active Directory (Azure AD), do której zostaną przyłączone maszyny wirtualne.  Użytkownicy muszą być członkami tej usługi Azure AD.  Istnieją dwie opcje implementacji usługi Azure AD:
- Usługi katalogowe usługi Azure AD.  Dla większości użytkowników jest to łatwiejsza opcja do zaimplementowania.
- Maszyna wirtualna z uruchomieniem promo kontrolera domeny.  Ta opcja wymaga więcej pracy, aby skonfigurować, ale oferuje większości użytkowników niższe koszty operacyjne.
Aby wyświetlić pełną listę wymagań wstępnych dotyczących korzystania z pulpitu wirtualnego systemu Windows, odwiedź [stronę przeglądu](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)pulpitu wirtualnego systemu Windows . 

## <a name="get-started"></a>Rozpoczęcie pracy 
Gdy wszystkie wymagania wstępne są na miejscu, należy wykonać kilka akcji, aby uzyskać implementacji w miejscu.  Zapoznaj się z tymi samouczkami, aby rozpocząć:
- [Tworzenie dzierżawy pulpitu wirtualnego systemu Windows](https://docs.microsoft.com/azure/virtual-desktop/tenant-setup-azure-active-directory)
- [Tworzenie puli hostów](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace) przy użyciu portalu Azure
- [Zarządzanie grupami aplikacji](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups) dla pulpitu wirtualnego systemu Windows

## <a name="eligibility"></a>Kwalifikowalności
| Poziom subskrypcji                                                 |     Kanały                                            | Korzyść                                                          | Odnawialnej?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (standard)   | VL, Azure, Handel detaliczny, | Dostępne|  Tak          |
| Visual Studio Enterprise z gitHub Enterprise  | Vl | Dostępne|  Tak          |
| Visual Studio Professional (standard) | VL, Azure, Handel detaliczny                                       | Dostępne                                                             |  Tak             |
| Visual Studio Professional z gitHub Enterprise | Vl                                       | Dostępne                                        |  Tak           |
| Visual Studio Test Professional (standard)                         | VL, Handel detaliczny                                              | Dostępne|  Tak          |
| Platformy MSDN (standard)                                          | VL, Handel detaliczny                                              | Dostępne                                         |  Tak          |
| Visual Studio Enterprise (standard)  | NFR<sup>1</sup> |Niedostępne  | Nie dotyczy |
| Visual Studio Enterprise, Visual Studio Professional (chmura miesięczna) | Azure | Niedostępne | Nie dotyczy |

<sup>1</sup>  *Obejmuje: Nie do odsprzedaży (NFR), FTE, Most Valuable Professional (MVP), Regional Director (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine*

> [!NOTE]
> Firma Microsoft nie oferuje już rocznych subskrypcji programu Visual Studio Professional i rocznych subskrypcji programu Visual Studio Enterprise w subskrypcjach w chmurze. Nie będzie żadnych zmian w istniejącym doświadczeniu klientów i możliwości odnawiania, zwiększania, zmniejszania lub anulowania subskrypcji. Zachęcamy nowych klientów, [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) aby przejść do eksplorowania różnych opcji zakupu programu Visual Studio.

Nie wiesz, której subskrypcji używasz?  Połącz [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) się, aby wyświetlić wszystkie subskrypcje przypisane do Twojego adresu e-mail. Jeśli nie widzisz wszystkich subskrypcji, możesz mieć jeden lub więcej przypisanych do innego adresu e-mail.  Aby wyświetlić te subskrypcje, musisz zalogować się przy tym adresie e-mail.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja pulpitu wirtualnego systemu Windows](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Następne kroki
-   Jeśli chcesz kupić subskrypcje programu Visual Studio, wyewidencjonuj:
     - [Ceny zakupów detalicznych](https://visualstudio.microsoft.com/vs/pricing/) za pośrednictwem sklepu Microsoft Store
     - [Programy licencjonowania zbiorowego](https://www.microsoft.com/licensing/default)
-   Dowiedz się więcej o [pulpicie wirtualnym systemu Windows](https://docs.microsoft.com/azure/virtual-desktop/overview) 
