---
title: Galerie prywatne | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027181d16024964d5487be2b3eb0b4ca261f98e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433609"
---
# <a name="private-galleries"></a>Galerie prywatne
Możesz udostępnić formanty, szablony i narzędzia, które tworzysz, publikując je do *prywatną galerię* w sieci intranet dla całej organizacji, w następujący sposób:

- Utwórz Atom () kanału informacyjnego RSS do odpowiednio skonfigurowanego centralną lokalizację (repozytorium) w sieci intranet. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie źródła danych dla galerii prywatnej Atom](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Dystrybucja *.pkgdef* pliku, który opisuje prywatną galerię. Firma Microsoft zaleca tej konfiguracji dla administratorów, którzy chcą nawiązać ona prywatną galerię na wielu komputerach jednocześnie.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Dodawanie galerii prywatnej rozszerzenia i aktualizacje w programie Visual Studio
 Po udostępnieniu ona prywatną galerię można dodać go do **rozszerzenia i aktualizacje** w programie Visual Studio.

 ![Okno dialogowe dodawania Menedżera rozszerzenia](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Aby dodać ona prywatną galerię do rozszerzenia i aktualizacje

1. Na pasku menu wybierz **narzędzia** > **opcje**.

2. W **środowiska** węzeł **rozszerzenia i aktualizacje**.

3. Wybierz **Dodaj** przycisku.

4. W **nazwa** na przykład wprowadź nazwę dla galerii prywatnej `My Gallery`.

5. W **adresu URL** wprowadź adres URL strumieniowego źródła Atom lub witryny programu SharePoint, który jest hostem prywatną galerię.

    1. Jeśli host znajduje się źródło danych Atom łączący się z prywatną galerię, adres URL będzie przypominać ten: http://www.mywebsite/mygallery/atom.xml.  Ten adres URL może odwoływać się do pliku lub ścieżkę sieciową.

    2. Jeśli host jest witryną programu SharePoint, adres URL będzie podobny do tego: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.

### <a name="manage-private-galleries"></a>Zarządzanie galerie prywatne
 Administrator może udostępnić ona prywatną galerię na kilku komputerach jednocześnie przez modyfikację rejestru systemu na każdym komputerze. Aby to zrobić, należy utworzyć *.pkgdef* pliku, który opisuje nowych kluczy rejestru i ich wartości.  Format ten plik jest w następujący sposób.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie galerią prywatnej za pomocą ustawień rejestru](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Zainstalować rozszerzenia z galerii prywatnej
 Można wyszukać i zainstalować rozszerzenia programu Visual Studio z prywatną galerię w **rozszerzenia i aktualizacje**. Użyto ona prywatną galerię o nazwie `My Gallery`.

 ![Menedżer rozszerzeń instalowanie galerią prywatną](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Aby wyszukać i zainstalować rozszerzenia z galerii prywatnej

1. Na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

2. W okienku po lewej stronie wybierz **rozszerzeń Online**, a następnie wybierz pozycję **Moja Galeria**.

3. W okienku po prawej stronie zaznacz rozszerzenie, a następnie wybierz **Pobierz** przycisku.

## <a name="update-extensions-from-a-private-gallery"></a>Aktualizuj rozszerzenia z galerii prywatnej
 Jak nowe wersje rozszerzeń programu Visual Studio są ogłaszane w galerii prywatnej, należy zaktualizować rozszerzenia, które zostały zainstalowane. Użyto ona prywatną galerię o nazwie `My Repository`.

 ![Aktualizacja galerii prywatnej Menedżer rozszerzenia](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Aby zaktualizować zainstalowanego rozszerzenia z galerii prywatnej

1. Na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

2. W okienku po lewej stronie wybierz **aktualizacje**, a następnie wybierz pozycję **Moje repozytorium**.

3. W okienku po prawej stronie zaznacz rozszerzenie, a następnie wybierz **aktualizacji** przycisku.

## <a name="see-also"></a>Zobacz także
- [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)