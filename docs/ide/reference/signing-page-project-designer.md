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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d4fa326d65606fd06d41fc5c697b80a526c1059
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461291"
---
# <a name="signing-page-project-designer"></a>Strona podpisywania, Projektant projektu

Na stronie  podpisywanie **projektanta projektu** można podpisać aplikacje i manifesty wdrażania, a także podpisać zestaw (podpisywanie silnej nazwy).

Należy zauważyć, że podpisywanie aplikacji i manifestów wdrożenia jest procesem odrębnym od podpisywania zestawu, chociaż oba zadania są wykonywane na stronie **podpisywania** .

Ponadto przechowywanie informacji o plikach klucza różni się w przypadku podpisywania manifestu i podpisywania zestawu. W przypadku podpisywania manifestu informacje o kluczu są przechowywane w bazie danych magazynu kryptograficznego komputera i w magazynie certyfikatów systemu Windows bieżącego użytkownika. W przypadku podpisywania zestawu kluczowe informacje są przechowywane tylko w bazie danych magazynu kryptograficznego komputera.

Aby uzyskać dostęp do strony **podpisywania** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Właściwości**. Gdy pojawi się **Projektant projektu** , kliknij kartę  podpisywanie.

## <a name="application-and-deployment-manifest-signing"></a>Podpisywanie manifestu aplikacji i wdrożenia

Pole wyboru **Podpisz manifesty ClickOnce**

Zaznacz to pole wyboru, aby podpisać aplikacje i manifesty wdrożenia za pomocą pary kluczy publicznych/prywatnych. Aby uzyskać więcej informacji o tym, jak to zrobić [, zobacz How to: Podpisywanie aplikacji i manifestów](../../ide/how-to-sign-application-and-deployment-manifests.md)wdrożenia.

Przycisk **Wybierz z magazynu**

Pozwala wybrać istniejący certyfikat z osobistego magazynu certyfikatów bieżącego użytkownika. Możesz wybrać jeden z tych certyfikatów do podpisywania aplikacji i manifestów wdrożenia.

Kliknięcie pozycji **Wybierz ze sklepu** spowoduje otwarcie okna dialogowego **Wybieranie certyfikatu** zawierającego listę certyfikatów w osobistym magazynie certyfikatów, które są aktualnie prawidłowe (nie wygasłe) i które mają klucze prywatne. Wybrany certyfikat powinien obejmować podpisywanie kodu.

Kliknięcie przycisku **Wyświetl właściwości certyfikatu**spowoduje wyświetlenie okna dialogowego **Szczegóły certyfikatu** . To okno dialogowe zawiera szczegółowe informacje o certyfikacie i zawiera dodatkowe opcje. Aby wyświetlić dodatkowe informacje pomocy, kliknij pozycję **Dowiedz się więcej o certyfikatach** .

Przycisk **Wybierz z pliku**

Umożliwia wybranie certyfikatu z istniejącego pliku klucza.

Kliknięcie przycisku **Wybierz z pliku** otwiera okno dialogowe **Wybieranie pliku** , które umożliwia wybranie pliku klucza certyfikatu (pfx). Plik musi być chroniony hasłem i nie może już znajdować się w osobistym magazynie certyfikatów.

W oknie dialogowym **Wprowadź hasło, aby otworzyć plik** wprowadź hasło, aby otworzyć plik klucza certyfikatu (pfx). Informacje o haśle są przechowywane na liście kontenerów kluczy osobistych i w osobistym magazynie certyfikatów.

Przycisk **tworzenia certyfikatu testowego**

Umożliwia utworzenie certyfikatu do testowania. Certyfikat testowy jest używany do podpisywania aplikacji ClickOnce i manifestów wdrożenia.

Kliknięcie przycisku **Utwórz certyfikat testowy** otwiera okno dialogowe **Tworzenie certyfikatu testowego** , w którym można wpisać hasło dla pliku klucza o silnej nazwie dla certyfikatu testowego. Plik ma nazwę *ProjectName*_TemporaryKey. pfx. Jeśli klikniesz przycisk **OK** bez wpisywania hasła, plik PFX nie jest szyfrowany hasłem.

Pole **adresu URL serwera znacznika czasowego**

Określa adres serwera, który sygnatura czasowa sygnatury. Po podaniu certyfikatu ta lokacja zewnętrzna weryfikuje czas, w którym aplikacja została podpisana.

## <a name="assembly-signing"></a>Podpisywanie zestawów

Pole wyboru **podpisz zestaw**

Zaznacz to pole wyboru, aby podpisać zestaw i utworzyć silnie nazwany plik klucza. Aby uzyskać więcej informacji na temat podpisywania zestawu przy użyciu **projektanta projektu**, zobacz [How to: Podpisz zestaw (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio).

Ta opcja używa narzędzia Al. exe dostarczonego przez zestaw Windows Software Development Kit (SDK) do podpisywania zestawu. Aby uzyskać więcej informacji na temat programu Al. [exe, zobacz How to: Podpisz zestaw silną nazwą](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

**Wybierz listę plików klucza o silnej nazwie**

Umożliwia określenie nowego lub istniejącego silnego pliku klucza, który jest używany do podpisywania zestawu. Wybierz pozycję  **\<Przeglądaj... >** wybrać istniejący plik klucza.

Wybierz pozycję  **\<nowy... >** utworzyć nowy plik klucza, za pomocą którego ma zostać podpisywany zestaw. Zostanie wyświetlone okno dialogowe **Tworzenie klucza silnej nazwy** , za pomocą którego można określić nazwę pliku klucza i chronić plik klucza hasłem. Hasło musi mieć długość co najmniej 6 znaków. Jeśli określisz hasło, zostanie utworzony plik wymiany informacji osobistych (pfx). Jeśli nie określisz hasła, zostanie utworzony plik o silnej nazwie (. snk).

Przycisk **zmiany hasła**

Zmienia hasło pliku klucza wymiany informacji osobistych (pfx), który jest używany do podpisywania zestawu.

Kliknięcie przycisku **Zmień hasło** otwiera okno dialogowe **Zmień hasło klucza** . W tym oknie dialogowym **stare hasło** jest bieżącym hasłem dla pliku klucza. **Nowe hasło** musi mieć długość co najmniej 6 znaków. Informacje o haśle są przechowywane w magazynie certyfikatów systemu Windows bieżącego użytkownika.

Pole wyboru **Opóźnij tylko znakowanie**

Zaznacz to pole wyboru, aby włączyć podpisywanie opóźnienia.

Należy zauważyć, że podpisany z opóźnieniem projekt nie zostanie uruchomiony i nie będzie można go debugować. Można jednak użyć programu [SN. exe (Narzędzie silnej nazwy)](/dotnet/framework/tools/sn-exe-strong-name-tool) z `-Vr` opcją pominięcia weryfikacji podczas opracowywania.

> [!NOTE]
> Po podpisaniu zestawu użytkownik może nie mieć zawsze dostępu do klucza prywatnego. Na przykład organizacja może mieć silnie chronioną parę kluczy, dla których deweloperzy nie mają dostępu codziennie. Klucz publiczny może być dostępny, ale dostęp do klucza prywatnego jest ograniczony do kilku osób. W takim przypadku można użyć opóźnionego lub  częściowego *podpisywania* , aby podać klucz publiczny, odwołując dodanie klucza prywatnego do momentu, gdy zestaw nie zostanie przekazany.

## <a name="see-also"></a>Zobacz także

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Zarządzanie podpisywaniem zestawu i manifestu](../../ide/managing-assembly-and-manifest-signing.md)
- [Instrukcje: Podpisywanie manifestów wdrożenia i aplikacji](../../ide/how-to-sign-application-and-deployment-manifests.md)
- [Instrukcje: Podpisz zestaw (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)
- [Instrukcje: Podpisz zestaw silną nazwą](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)