---
title: Utwórz skojarzenia plików (Aplikacja ClickOnce)
description: Dowiedz się, jak skojarzyć aplikację ClickOnce z co najmniej jednym rozszerzeniem nazwy pliku, aby aplikacja była uruchamiana, gdy użytkownik otworzy taki plik.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b74e20d21ad2c67eed36add90051119c7b8b56e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861169"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Instrukcje: tworzenie skojarzeń plików dla aplikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje mogą być skojarzone z jednym lub więcej rozszerzeniami nazw plików, dzięki czemu aplikacja zostanie uruchomiona automatycznie, gdy użytkownik otworzy plik tych typów. Dodawanie obsługi rozszerzenia nazwy pliku do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji jest proste.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Aby utworzyć skojarzenia plików dla aplikacji ClickOnce

1. Utwórz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację normalnie lub Użyj istniejącej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

2. Otwórz manifest aplikacji za pomocą edytora tekstu lub XML, takiego jak Notatnik.

3. Znajdź `assembly` element. Aby uzyskać więcej informacji, zobacz [manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).

4. Jako element podrzędny `assembly` elementu Dodaj `fileAssociation` element. `fileAssociation`Element ma cztery atrybuty:

   - `extension`: Rozszerzenie nazwy pliku, które chcesz skojarzyć z aplikacją.

   - `description`: Opis typu pliku, który będzie wyświetlany w powłoce systemu Windows.

   - `progid`: Ciąg unikatowo identyfikujący typ pliku, aby oznaczyć go w rejestrze.

   - `defaultIcon`: Ikona do użycia dla tego typu pliku. Ikona musi być dodana jako zasób pliku w manifeście aplikacji. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Dołączanie pliku danych do aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Aby zapoznać się z przykładem `file` `fileAssociation` elementów i, zobacz [ \<fileAssociation> element](../deployment/fileassociation-element-clickonce-application.md).

5. Jeśli chcesz skojarzyć więcej niż jeden typ pliku z aplikacją, Dodaj dodatkowe `fileAssociation` elementy. Należy zauważyć, że `progid` atrybut powinien być różny dla każdego.

6. Po zakończeniu pracy z manifestem aplikacji ponownie podpisz manifest. Można to zrobić z poziomu wiersza polecenia, używając *Mage.exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Aby uzyskać więcej informacji, zobacz [Mage.exe (narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Zobacz też
- [\<fileAssociation> postaci](../deployment/fileassociation-element-clickonce-application.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (Narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)