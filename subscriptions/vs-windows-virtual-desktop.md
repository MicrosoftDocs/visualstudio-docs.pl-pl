---
title: Microsoft Windows Virtual Desktop w subskrypcjach programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 03/17/2021
ms.topic: conceptual
description: Dowiedz się, jak korzystać z pulpitu wirtualnego systemu Microsoft Windows za pośrednictwem subskrypcji programu Visual Studio
ms.openlocfilehash: 2e7aad5d3f8214d39e5671e4bf5c4d5d357cd930
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671742"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Dostęp do pulpitu wirtualnego systemu Windows w subskrypcjach 
Subskrybenci programu Visual Studio mogą teraz korzystać z indywidualnych środków na korzystanie z platformy Azure do tworzenia i testowania usług pulpitu wirtualnego systemu Microsoft Windows.  
Windows Virtual Desktop to kompleksowa usługa wirtualizacji pulpitu i aplikacji działająca w chmurze. Jest to jedyna Infrastruktura pulpitu wirtualnego (VDI), która oferuje uproszczone zarządzanie, wielosesyjne Windows 10, optymalizacje dla Microsoft 365 aplikacji dla przedsiębiorstw i obsługę środowisk Usługi pulpitu zdalnego (RDS). Wdrażaj i Skaluj komputery stacjonarne i aplikacje z systemem Windows na platformie Azure w ciągu kilku minut i korzystaj z wbudowanych funkcji zabezpieczeń i zgodności.
Oto co można zrobić w przypadku uruchamiania pulpitu wirtualnego systemu Windows na platformie Azure:
- Konfigurowanie wdrożenia obejmującego wiele sesji systemu Windows 10, które zapewnia pełną skalowalność systemu Windows 10
- Wirtualizacja Microsoft 365 aplikacje dla przedsiębiorstw i optymalizacja do działania w scenariuszach wirtualnych obejmujących wiele użytkowników
- Udostępnianie pulpitów wirtualnych systemu Windows 7 z bezpłatnymi rozszerzonymi aktualizacjami zabezpieczeń
- Przenoszenie istniejących Usługi pulpitu zdalnego (RDS) i komputerów stacjonarnych i aplikacji z systemem Windows Server do dowolnego komputera
- Wirtualizacja zarówno komputerów stacjonarnych, jak i aplikacji
- Zarządzanie komputerami stacjonarnymi i aplikacjami z systemem Windows 10, Windows Server i Windows 7 za pomocą ujednoliconego środowiska zarządzania, aby uzyskać więcej informacji na temat tego, co można zrobić z pulpitem wirtualnym systemu Windows, Obejrzyj wprowadzenie [wideo](/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Korzystanie z pulpitu wirtualnego systemu Windows z platformą Azure 
Subskrybenci programu Visual Studio mają teraz kilka sposobów na korzystanie z subskrypcji platformy Azure w celu płacenia za usługi pulpitu wirtualnego systemu Windows:
- [Poszczególne kredyty na platformie Azure DevTest](vs-azure.md).  Subskrybenci, którzy otrzymują pojedyncze kredyty na korzystanie z usługi Azure DevTest w ramach swoich subskrypcji, mogą używać tych kredytów do płacenia za usługi pulpitu wirtualnego systemu Windows.  Kwota miesięcznego kredytu zależy od poziomu subskrypcji.
- [Subskrypcje usługi Azure DevTest — płatność zgodnie](vs-azure-payg.md)z rzeczywistym użyciem.  Możesz utworzyć subskrypcje platformy Azure i dołączyć instrument płatniczy, aby bezproblemowo zapłacić za użycie pulpitu wirtualnego systemu Windows. 
- [Oferta usługi Azure Enterprise Agreement DevTest](azure-ea-devtest.md).  Dzięki tej ofercie Subskrybenci z umowami Enterprise Agreement mogą skorzystać z usług pulpitu wirtualnego systemu Windows przy obniżonych cenach na platformę Azure. 

## <a name="requirements"></a>Wymagania
Pulpit wirtualny systemu Windows wymaga Azure Active Directory (Azure AD), do którego zostaną dołączone maszyny wirtualne.  Użytkownicy muszą należeć do tej usługi Azure AD.  Dostępne są dwie opcje wdrożenia usługi Azure AD:
- Usługi katalogowe usługi Azure AD.  W przypadku większości użytkowników jest to prostsze rozwiązanie do implementowania.
- Maszyna wirtualna z uruchomioną funkcją awansowania kontrolera domeny.  Ta opcja wymaga większego nakładu pracy w konfiguracji, ale oferuje większości użytkownikom niższy koszt działania.
Aby zapoznać się z pełną listą wymagań wstępnych dotyczących korzystania z pulpitu wirtualnego systemu Windows, odwiedź [stronę Omówienie](/azure/virtual-desktop/overview#requirements)pulpitu wirtualnego systemu Windows. 

## <a name="get-started"></a>Rozpoczęcie pracy 
Gdy zostaną spełnione wszystkie wymagania wstępne, należy wykonać kilka czynności w celu wprowadzenia implementacji.  Zapoznaj się z tymi samouczkami, aby rozpocząć pracę:
- [Tworzenie dzierżawy pulpitu wirtualnego systemu Windows](/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- [Tworzenie puli hostów](/azure/virtual-desktop/create-host-pools-azure-marketplace) przy użyciu Azure Portal
- [Zarządzanie grupami aplikacji](/azure/virtual-desktop/manage-app-groups) dla pulpitu wirtualnego systemu Windows

## <a name="eligibility"></a>Kryteria
| Poziom subskrypcji                                                 |     Kanały                                            | Korzyść                                                          | Odnawialny?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (standardowa)   | LICENCJONOWANie, Azure, sprzedaż detaliczna, | Dostępne|  Tak          |
| Visual Studio Enterprise subskrypcję z usługą GitHub Enterprise  | Licencja | Dostępne|  Tak          |
| Visual Studio Professional (standardowa) | LICENCJONOWANie, Azure, sprzedaż detaliczna                                       | Dostępne                                                             |  Tak             |
| Visual Studio Professional subskrypcję z usługą GitHub Enterprise | Licencja                                       | Dostępne                                        |  Tak           |
| Visual Studio Test Professional (standardowa)                         | LICENCJONOWANie detaliczne                                              | Dostępne|  Tak          |
| Platformy MSDN (standardowa)                                          | LICENCJONOWANie detaliczne                                              | Dostępne                                         |  Tak          |
| Visual Studio Enterprise (standardowa)  | NFR<sup>1</sup> |Niedostępne  | Nie dotyczy |
| Visual Studio Enterprise, Visual Studio Professional (chmura miesięczna) | Azure | Niedostępne | Nie dotyczy |

<sup>1</sup>  *obejmuje: nie do odsprzedaży (NFR), ekwiwalentu, najbardziej cennych profesjonalistów (MVP), regionalnego dyrektora (RD), Microsoft Partner Network (MPN), Visual Studio Industry partner (VSIP), Microsoft Certified Trainer, BizSpark, Wyobraź sobie, NFR Basic*

> [!NOTE]
> Firma Microsoft nie oferuje już Visual Studio Professional rocznych subskrypcji i Visual Studio Enterprise rocznych subskrypcji w ramach subskrypcji chmury. Istnieją zmiany w istniejących klientach i możliwość odnowienia, zwiększenia, zmniejszenia lub anulowania subskrypcji. Zachęcamy nowych klientów do [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) przeglądania różnych opcji zakupu programu Visual Studio.

Nie masz pewności, której subskrypcji używasz?  Połącz się z, [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) Aby wyświetlić wszystkie subskrypcje przypisane do Twojego adresu e-mail. Jeśli nie widzisz wszystkich subskrypcji, być może masz co najmniej jeden przypisany do innego adresu e-mail.  Musisz zalogować się przy użyciu tego adresu e-mail, aby zobaczyć te subskrypcje.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja usługi Windows Virtual Desktop](/azure/virtual-desktop/)
- [Obsługa subskrypcji programu Visual Studio](https://my.visualstudio.com/gethelp)

## <a name="next-steps"></a>Następne kroki
-   Jeśli musisz kupić subskrypcje programu Visual Studio, zapoznaj się z tematem:
     - [Cennik zakupów detalicznych](https://visualstudio.microsoft.com/vs/pricing/) za pomocą Microsoft Store
     - [Programy licencjonowania zbiorowego](https://www.microsoft.com/licensing/default)
-   Więcej informacji na temat [pulpitu wirtualnego systemu Windows](/azure/virtual-desktop/overview)