---
title: Wywoływanie modeli obiektów SharePoint | Dokumentacja firmy Microsoft
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24634143a40f7b163c0b658bddb5596041868033
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988410"
---
# <a name="call-into-the-sharepoint-object-models"></a>Wywoływanie modeli obiektów SharePoint
  Po utworzeniu rozszerzeń dla narzędzi SharePoint w programie Visual Studio może być do wywoływania interfejsów API programu SharePoint do wykonywania określonych zadań. Na przykład jeśli utworzysz niestandardowego kroku wdrożenia dla projektów programu SharePoint, może być konieczne wywoływanie interfejsów API programu SharePoint do wykonania niektórych zadań w celu wdrażania rozwiązań z zakresu.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zapewnia dwa różne modele obiektów używanych w rozszerzenia narzędzi programu SharePoint: modelu obiektów serwera i modelu obiektów klienta. Każdy model obiektu ma zalety i wady w kontekście rozszerzenia narzędzi programu SharePoint.

 Aby zapoznać się z omówieniem modeli obiektów SharePoint, zobacz [omówienie modelu programowania programu SharePoint rozszerzeń narzędzi](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Korzystanie z modelu obiektów klienta w projektach rozszerzenia
 Podczas opracowywania rozszerzeń dla narzędzi SharePoint można użyć modelu obiektów klienta w projekcie, takich jak dowolnego innego zestawu zarządzanych interfejsów API. W modelu obiektów klienta można dodać odwołania do zestawów, do projektu, a w modelu obiektów klienta mogą wywoływać interfejsy API bezpośrednio w kodzie.

 Jednak client object model ma dwie wady w kontekście rozszerzenia narzędzi programu SharePoint:

- Client object model zawiera tylko podzbiór modelu obiektów serwera. Jeśli musisz korzystać z funkcji programu SharePoint, która nie jest widoczna w modelu obiektów klienta, należy użyć modelu obiektów serwera.

- Mimo że w rozszerzenia narzędzi programu SharePoint przy użyciu client object model powinny działać w większości przypadków, mogą wystąpić sytuacje, w którym wywołania modelu obiektów klienta nie działają zgodnie z oczekiwaniami. Client object model jest przeznaczony do użycia w aplikacjach klienckich do wywołania w witrynach programu SharePoint na serwerze zdalnym lub w farmie. Narzędzia programu SharePoint w programie Visual Studio działa tylko w przypadku lokalnej instalacji programu SharePoint na komputerze deweloperskim. W związku z tym gdy korzystasz z modelu obiektów klienta w rozszerzenia narzędzi programu SharePoint, możesz wywołać w witrynie programu SharePoint na komputerze lokalnym, który jest nie jak client object model został zaprojektowany do użycia.

  Aby uzyskać wskazówki, który demonstruje sposób skorzystania z modelu obiektów klienta do rozszerzenia narzędzi programu SharePoint w programie Visual Studio, zobacz [instruktażu: Wywołania w modelu obiektu klienta SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Użyj modelu obiektów serwera w projektach rozszerzenia
 W modelu obiektów serwera jest nadzbiorem modelu obiektów klienta. Korzystając z modelu obiektów serwera, można użyć wszystkich funkcji, [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ujawnić programowo.

 Rozszerzenia narzędzi programu SharePoint mogą używać interfejsów API w modelu obiektów serwera, ale ich nie można bezpośrednio wywoływać interfejsy API. W modelu obiektów serwera może być wywołana tylko z procesu 64-bitowego przeznaczonego programu .NET Framework 3.5. Rozszerzenia narzędzi programu SharePoint wymagają jednak [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] są uruchamiane w procesie 32-bitowego programu Visual Studio. Zapobiega to bezpośrednio odwołuje się do zestawów w modelu obiektów serwera SharePoint rozszerzenia narzędzi programu SharePoint.

 Jeśli chcesz użyć modelu obiektów serwera w rozszerzenia narzędzi programu SharePoint, należy utworzyć niestandardowy *polecenia SharePoint* wywołać interfejs API. Polecenie programu SharePoint należy zdefiniować w pomocniczego zestawu, który można wywoływać bezpośrednio do modelu obiektów serwera. W projekcie rozszerzenia możesz wywołać polecenie programu SharePoint pośrednio za pomocą metody ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu.

 Aby uzyskać więcej informacji na temat tworzenia i używania poleceń programu SharePoint, zobacz [jak: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) i [jak: Wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Aby uzyskać informacje o sposobie wdrażania poleceń programu SharePoint, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Aby uzyskać wskazówki dotyczące pokazują, jak utworzyć i używać poleceń programu SharePoint, zobacz [instruktażu: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) i [instruktażu: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Zrozumienie, jak są wykonywane polecenia programu SharePoint
 Zestawy, które definiują poleceń programu SharePoint są załadowane w procesie 64-bitowego hosta o nazwie *vssphost4.exe*. Po wywołaniu polecenia programu SharePoint w rozszerzenia narzędzi programu SharePoint, polecenie jest wykonywane przez *vssphost4.exe* zamiast 32-bitowego procesu programu Visual Studio (*devenv.exe*). Można kontrolować niektóre aspekty jak poleceń programu SharePoint są wykonywane przez ustawienie wartości w rejestrze. Aby uzyskać więcej informacji, zobacz [Debugowanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Instrukcje: Wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Omówienie modelu programowania programu SharePoint rozszerzeń narzędzi](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
