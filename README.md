# UPOZORNĚNÍ: Tento projekt je zatím ve vývoji, nefunguje.
# Zranitelnost v dockeru
V dockeru je zranitelnost, ketrá způsobuje, že pokud docker běží jako root, může kdokoliv, kdo má přístup k jeho socketu, získat root práva, bez ohledu na konfiguraci. Docker sice umožňuje nastavit výchozí seccomp nebo AppArmor profil, ale uživatel může použít jiný pomocí přepínače `--security-opt seccomp=<nějaký nezabezpečenný profil>`. Proto jsem se rozhodl vytvořit svůj vlastní ebpf program, který jsem pojmenoval securenux a alternativní verzi dockeru, která ho podporuje. Securenux bude podporovat priority profilů, takže si uživatel bude moci nastavit svůj profil, v zásadních věcech ale bude mít přednost výchozí profil.

# Použití
Spusťte následující příkazy:

    git clone https://github.com/moby/moby.git docker_alt
    git clone https://github.com/reudej/docker_alt.git
    make
    sudo make install

