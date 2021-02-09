---
title: Wywoływanie modeli obiektów programu SharePoint | Microsoft Docs
description: Dowiedz się, jak wywoływać dwa różne modele obiektów, których można użyć w rozszerzeniach narzędzi programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14358b5cc84f63227fd5001731c261002a324492
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928942"
---
# <a name="call-into-the-sharepoint-object-models"></a>Wywoływanie modeli obiektów programu SharePoint
  Podczas tworzenia rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio, może być konieczne wywołanie interfejsów API programu SharePoint w celu wykonania określonych zadań. Jeśli na przykład utworzysz niestandardowy krok wdrożenia dla projektów programu SharePoint, może być konieczne wywołanie interfejsów API programu SharePoint w celu wykonania niektórych zadań związanych z wdrażaniem rozwiązań.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] udostępniamy dwa różne modele obiektów, których można używać w rozszerzeniach narzędzi programu SharePoint: model obiektów serwera i model obiektów klienta. Każdy model obiektów ma zalety i wady w kontekście rozszerzeń narzędzi programu SharePoint.

 Aby zapoznać się z omówieniem modeli obiektów programu SharePoint, zobacz [Omówienie modelu programowania rozszerzeń narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Używanie modelu obiektów klienta w projektach rozszerzeń
 Podczas tworzenia rozszerzenia dla narzędzi programu SharePoint można użyć modelu obiektów klienta w projekcie, podobnie jak każdy inny zestaw zarządzanych interfejsów API. Można dodać odwołania do zestawów w modelu obiektów klienta do projektu i można wywołać interfejsy API w modelu obiektów klienta bezpośrednio z poziomu kodu.

 Jednak model obiektów klienta ma dwa wady w kontekście rozszerzeń narzędzi programu SharePoint:

- Model obiektów klienta zawiera tylko podzestaw modelu obiektów serwera. Jeśli musisz użyć funkcji programu SharePoint, która nie jest dostępna w modelu obiektów klienta, należy użyć modelu obiektów serwera.

- Chociaż użycie modelu obiektów klienta w rozszerzeniach narzędzi programu SharePoint powinno być wykonywane w większości przypadków, może wystąpić kilka scenariuszy, w których wywołania modelu obiektów klienta nie działają zgodnie z oczekiwaniami. Model obiektów klienta jest przeznaczony do użycia w aplikacjach klienckich do wywoływania w witrynach programu SharePoint na serwerze zdalnym lub w farmie. Narzędzia programu SharePoint w programie Visual Studio działają tylko z lokalną instalacją programu SharePoint na komputerze deweloperskim. W związku z tym, w przypadku używania modelu obiektów klienta w rozszerzeniu narzędzi programu SharePoint, należy wywołać witrynę programu SharePoint na komputerze lokalnym, która nie jest przeznaczona do użycia przez model obiektów klienta.

  Aby zapoznać się z przewodnikiem, który pokazuje, jak używać modelu obiektów klienta w rozszerzeniu narzędzi programu SharePoint w programie Visual Studio, zobacz [Przewodnik: wywoływanie modelu obiektów klienta programu SharePoint w rozszerzeniu Eksplorator serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Korzystanie z modelu obiektów serwera w projektach rozszerzeń
 Model obiektów serwera jest nadzbiorem modelu obiektów klienta. Korzystając z modelu obiektów serwera, można korzystać ze wszystkich funkcji, które udostępniają [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] program [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] programowo.

 Rozszerzenia narzędzi programu SharePoint mogą używać interfejsów API w modelu obiektów serwera, ale nie mogą bezpośrednio wywoływać interfejsów API. Model obiektów serwera można wywołać tylko z 64-bitowego procesu, który jest przeznaczony dla .NET Framework 3,5. Jednak rozszerzenia narzędzi programu SharePoint wymagają [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i są uruchamiane w procesie 32-bitowym programu Visual Studio. Zapobiega to bezpośrednio odwołującym się do zestawów w modelu obiektów programu SharePoint.

 Jeśli chcesz użyć modelu obiektów serwera w rozszerzeniu narzędzi programu SharePoint, musisz utworzyć niestandardowe *polecenie programu SharePoint* , aby wywołać interfejs API. Zdefiniuj polecenie programu SharePoint w zestawie pomocniczym, które może bezpośrednio wywołać model obiektów serwera. W projekcie rozszerzenia można wywołać polecenie programu SharePoint pośrednio przy użyciu metody ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu.

 Aby uzyskać więcej informacji na temat tworzenia i używania poleceń programu SharePoint, zobacz [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) i [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md). Aby uzyskać informacje na temat sposobu wdrażania poleceń programu SharePoint, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Aby zapoznać się z przewodnikami pokazującymi sposób tworzenia i używania poleceń programu SharePoint, zobacz [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) i [przewodników programu SharePoint: rozszerzona Eksplorator serwera, aby wyświetlić części sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Informacje o wykonywaniu poleceń programu SharePoint
 Zestawy, które definiują polecenia programu SharePoint, są ładowane w 64-bitowym procesie o nazwie *vssphost4.exe*. Po wywołaniu polecenia programu SharePoint w rozszerzeniu narzędzi programu SharePoint polecenie jest wykonywane przez *vssphost4.exe* zamiast 32-bitowego procesu programu Visual Studio (*devenv.exe*). Można kontrolować pewne aspekty sposobu wykonywania poleceń programu SharePoint przez ustawienie wartości w rejestrze. Aby uzyskać więcej informacji, zobacz [Debugowanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Instrukcje: wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Omówienie modelu programowania rozszerzeń narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
