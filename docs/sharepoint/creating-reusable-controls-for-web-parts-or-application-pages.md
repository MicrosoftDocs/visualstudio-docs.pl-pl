---
title: Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d042c42bae59c6dbf92f0e381444cc011b40db0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842827"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji
  W programie Visual Studio możesz utworzyć niestandardowe formanty wielokrotnego użytku, które mogą być wykorzystane przez strony aplikacji i składników Web Part, które są uruchamiane w programie SharePoint. Te kontrolki są nazywane kontrolki użytkownika. Formant użytkownika jest rodzajem złożonej kontrolki, która działa podobnie do strony sieci Web platformy ASP.NET — Dodawanie istniejących formantów serwera sieci Web i znaczników do formantu użytkownika i definiowanie właściwości i metody dla formantu. Następnie można osadzać na stronach sieci Web platformy ASP.NET, w których działają jako jednostka.  
  
## <a name="create-a-user-control"></a>Tworzenie kontrolki użytkownika
 Aby utworzyć kontrolkę użytkownika, należy dodać **kontrolki użytkownika** do **pusty projekt programu SharePoint**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie kontrolki użytkownika dla części strony lub sieci web aplikacji programu SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Po dodaniu **kontrolki użytkownika** element, tworzy folder w projekcie programu Visual Studio i następnie dodaje kilka plików do folderu. W poniższej tabeli opisano każdy plik.  
  
|Plik|Opis|  
|----------|-----------------|  
|Plik kontrolki użytkownika|Definiuje kontrolki użytkownika. Projektowanie kontrolki użytkownika, dodając formanty i znaczników do tego pliku.|  
|Plik kodu|Zawiera kod związany z kontrolki użytkownika. Dodaj kod do obsługi zdarzeń do tego pliku.|  
|Plik kodu projektanta|Zawiera kod generowany przez projektanta i nie należy bezpośrednio edytować.|  
  
## <a name="design-the-user-control"></a>Projektowanie kontrolki użytkownika
 Projektowanie kontrolki użytkownika przy użyciu projektanta Visual Web Developer w programie Visual Studio. Projektant jest wyświetlany, gdy otworzysz plik kontrolki użytkownika w projekcie i wybierz **projektowania** kartę.  

## <a name="consume-the-user-control"></a>Użyj kontrolki użytkownika
 Formanty użytkownika nie są wyświetlane w programie SharePoint, dopóki nie zostaną umieszczone na stronie aplikacji lub składnika Web Part.  
  
 Aby dołączyć kontrolki użytkownika na stronie aplikacji, otwórz strony sieci Web, do której chcesz dodać kontrolkę użytkownika ASP.NET. Przełącz do widoku projektu, a następnie wybierz swój plik formant użytkownika niestandardowego w Eksploratorze rozwiązań, a następnie przeciągnij go na stronie. Kontrolka użytkownika ASP.NET jest dodawany do strony, a projektant tworzy dyrektywy @ rejestru, który jest wymagany do strony aby rozpoznać kontrolki użytkownika. Teraz możesz pracować z właściwości publiczne i metod formantu.  
  
 Aby dołączyć kontrolki użytkownika w składniku Web Part, należy dodać kontrolkę użytkownika do składnika Web Part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> kolekcji w pliku kodu składnika Web Part. Poniższy przykład dodaje formant użytkownika do <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> zbiór składnika Web Part.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debug-a-user-control"></a>Debugowanie kontrolki użytkownika
 Aby debugować formant użytkownika, upewnij się, czy kontrolka użytkownika znajduje się w stronę aplikacji lub składnika Web Part w projekcie programu SharePoint. Następnie można debugować kodu w kontrolce użytkownika, tak samo, jak debuguje się kod w dowolnym projektu programu Visual Studio.  
  
 Po uruchomieniu debugera programu Visual Studio, Visual Studio otwiera witrynę programu SharePoint.  
  
 W programie SharePoint otwórz strony aplikacji, który zawiera formant użytkownika. Jeśli kontrolka użytkownika znajduje się w składniku Web Part, należy dodać składnik Web Part do strony składników Web Part w programie SharePoint.  
  
 Aby uzyskać więcej informacji na temat debugowania projektów programu SharePoint, zobacz [rozwiązań SharePoint Rozwiązywanie problemów z](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Tworzenie kontrolki użytkownika dla części strony lub sieci web aplikacji programu SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Dowiesz się, jak utworzyć niestandardowe formanty wielokrotnego użytku, które mogą być wykorzystane przez strony aplikacji i składników Web Part, które są uruchamiane w programie SharePoint.|  
