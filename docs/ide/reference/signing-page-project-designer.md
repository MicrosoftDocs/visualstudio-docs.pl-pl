---
title: Strona podpisywania, Projektant projektu
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 516e2aaf4a55ad6422200f9fef1cbbf2d435af7b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597337"
---
# <a name="signing-page-project-designer"></a>Strona podpisywania, Projektant projektu

Strona **Podpisywanie** **projektanta projektu** służy do podpisywania manifestów aplikacji i wdrażania, a także do podpisywania zestawu (podpisywanie silnej nazwy).

Należy zauważyć, że podpisywanie manifestów aplikacji i wdrażania jest procesem odrębnym od podpisywania zestawu, chociaż oba zadania są wykonywane na stronie **Podpisywanie.**

Ponadto przechowywanie informacji o pliku klucza różni się w przypadku podpisywania manifestu i podpisywania zestawu. W przypadku podpisywania manifestu kluczowe informacje są przechowywane w kryptograficznej bazie danych magazynu komputera i magazynie certyfikatów systemu Windows bieżącego użytkownika. W przypadku podpisywania zestawu kluczowe informacje są przechowywane tylko w kryptograficznej bazie danych magazynu komputera.

Aby uzyskać dostęp do strony **Podpisywanie,** wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie w menu **Projekt** kliknij polecenie **Właściwości**. Po wyświetleniu **projektanta projektu** kliknij kartę **Podpisywanie.**

## <a name="application-and-deployment-manifest-signing"></a>Podpisywanie manifestu aplikacji i wdrażania

Zaznacz pole wyboru **"Podpisz manifesty ClickOnce"**

Zaznacz to pole wyboru, aby podpisać manifesty aplikacji i wdrożenia za pomocą pary kluczy publicznych/prywatnych. Aby uzyskać więcej informacji na temat tego, zobacz [Jak: Podpisz manifesty aplikacji i wdrożenia](../../ide/how-to-sign-application-and-deployment-manifests.md).

**Wybierz z** przycisku Sklep

Umożliwia wybranie istniejącego certyfikatu z magazynu certyfikatów osobistych bieżącego użytkownika. Można wybrać jeden z tych certyfikatów, aby podpisać manifesty aplikacji i wdrażania.

Kliknięcie **przycisku Wybierz ze sklepu** powoduje otwarcie okna **dialogowego Wybieranie certyfikatu,** w którym wymieniono certyfikaty w osobistym magazynie certyfikatów, które są aktualnie prawidłowe (nie wygasły) i które mają klucze prywatne. Celem wybranego certyfikatu powinno być podpisywanie kodu.

Po **kliknięciu przycisku Wyświetl właściwości certyfikatu**zostanie wyświetlone okno dialogowe **Szczegóły certyfikatu.** To okno dialogowe zawiera szczegółowe informacje o certyfikacie i zawiera dodatkowe opcje. Możesz kliknąć kliknij dowiedz **się więcej o certyfikatach,** aby wyświetlić dodatkowe informacje o Pomocy.

Wybierz z **przycisku Plik**

Umożliwia wybranie certyfikatu z istniejącego pliku klucza.

Kliknięcie **przycisku Wybierz z pliku** powoduje otwarcie okna dialogowego **Wybieranie pliku,** które umożliwia wybranie pliku klucza certyfikatu (pfx). Plik musi być chroniony hasłem i nie może już znajdować się w osobistym magazynie certyfikatów.

W oknie dialogowym **Wprowadzanie hasła do otwierania pliku** wprowadź hasło, aby otworzyć plik klucza certyfikatu (pfx). Informacje o hasłach są przechowywane na osobistej liście kontenerów kluczy i osobistym magazynie certyfikatów.

Przycisk **Utwórz certyfikat testu**

Umożliwia utworzenie certyfikatu do testowania. Certyfikat testu jest używany do podpisywania clickonce aplikacji i manifestów wdrażania.

**Kliknięcie przycisku Utwórz certyfikat testu** powoduje otwarcie okna dialogowego **Tworzenie certyfikatu testowego,** w którym można wpisać hasło pliku klucza silnej nazwy certyfikatu testowego. Plik nosi nazwę *projectname*_TemporaryKey.pfx. Jeśli klikniesz **przycisk OK** bez wpisywania hasła, plik .pfx nie jest zaszyfrowany hasłem.

Pole **ADRESU URL serwera sygnatury** czasowej

Określa adres serwera, który sygnalizuje podpis. Po podaniu certyfikatu ta zewnętrzna lokacja weryfikuje czas podpisania aplikacji.

## <a name="assembly-signing"></a>Podpisywanie zestawu

**Podpisywanie** pola wyboru zestawu

Zaznacz to pole wyboru, aby podpisać zestaw i utworzyć plik klucza o silnie nazwanej nazwie. Aby uzyskać więcej informacji na temat podpisywania zestawu przy użyciu **projektanta projektu,** zobacz [Jak: Podpisz zestaw (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio).

Ta opcja używa narzędzia Al.exe dostarczonego przez zestaw Windows Software Development Kit (SDK) do podpisywania zestawu. Aby uzyskać więcej informacji na temat al.exe, zobacz [Jak: Podpisz zgromadzenie z silną nazwą](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

**Wybieranie listy plików klucza silnej nazwy**

Umożliwia określenie nowego lub istniejącego pliku klucza o silnie nazwanej nazwie, który jest używany do podpisywania zestawu. Wybierz ** \<opcję Przeglądaj...>,** aby wybrać istniejący plik klucza.

Wybierz ** \<pozycję Nowy...>,** aby utworzyć nowy plik klucza, za pomocą którego ma być podpisywanie złożenia. Zostanie wyświetlone okno dialogowe **Tworzenie klucza silnej nazwy,** za pomocą którego można określić nazwę pliku klucza i chronić plik klucza hasłem. Hasło musi mieć co najmniej 6 znaków. Jeśli określisz hasło, zostanie utworzony plik wymiany informacji osobistych (pfx); Jeśli hasło nie zostanie określone, zostanie utworzony plik o silnie nazwanym kluczu (.snk).

**Przycisk Zmień hasło**

Zmienia hasło pliku klucza wymiany informacji osobistych (pfx), który jest używany do podpisywania zestawu.

Kliknięcie **przycisku Zmień hasło** powoduje otwarcie okna dialogowego **Zmienianie hasła klucza.** W tym oknie dialogowym **Stare hasło** jest bieżącym hasłem dla pliku klucza. **Nowe hasło** musi mieć co najmniej 6 znaków. Informacje o haśle są przechowywane w magazynie certyfikatów systemu Windows bieżącego użytkownika.

**Tylko** pole wyboru Znak opóźnienia

Zaznacz to pole wyboru, aby włączyć podpisywanie opóźnień.

Należy zauważyć, że opóźnienie podpisane projektu nie zostanie uruchomiony i nie można debugować. Można jednak użyć [sn.exe (silnej nazwy narzędzie)](/dotnet/framework/tools/sn-exe-strong-name-tool) z `-Vr` opcją pominąć weryfikacji podczas tworzenia.

> [!NOTE]
> Podczas podpisywania zestawu, nie zawsze może mieć dostęp do klucza prywatnego. Na przykład organizacja może mieć ściśle strzeżoną parę kluczy, do których deweloperzy nie mają dostępu na co dzień. Klucz publiczny może być dostępny, ale dostęp do klucza prywatnego jest ograniczony do kilku osób. W takim przypadku można użyć *opóźnionego* lub *częściowego podpisania,* aby zapewnić klucz publiczny, odraczając dodanie klucza prywatnego, dopóki zestaw nie zostanie przekazany.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Zarządzanie zestawem i podpisywanie manifestu](../../ide/managing-assembly-and-manifest-signing.md)
- [Porady: podpisywanie aplikacji i manifestów wdrożenia](../../ide/how-to-sign-application-and-deployment-manifests.md)
- [Jak: Podpisz zestaw (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)
- [Instrukcje: podpisywanie zestawu silną nazwą](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)
