Lors de la [https://perlconference.us/]("Conference in the cloud"),
[Sawyer X](https://metacpan.org/search?q=XSAWYERX),
(pumpkin)[https://perldoc.perl.org/perlhist.html#PUMPKIN%3f] actuel
du langage [Perl](https://www.perl.org/] a annoncé que perl pasera
en version 7 dans moins d'un an.

> Perl 7 is going to be Perl 5.32 with different settings

C'est la première version majeure depuis le 17 octobre 1994 et pour
ceux qui n'ont pas suivi l'évolution de ce langage, Perl7 pourrait
passer pour un non-évenement. C'est au contraire un changement
qui provoque à la fois la colère et l'antousiame.

Le développement de Perl (et son schema de versions) a été contraint
par plusieurs réalités importantes.

La réécriture de Perl par sa communauté (Perl 6) a commencé au tout
début du millénaire pour aboutir à un langage dynamique dans lequel
perl n'est plus qu'une source d'inspiration parmis tant d'autres.
Un peu comme ruby qui se voulait être un "perl made right" s'appelle
bien "ruby", les membres de la communauté Perl6 ont finalement
rebaptisé leur création "raku" (#rakulang) en octobre 2019.

Pendant ces longues années, une partie de la communauté Perl a
continué à faire évoluer la version 5. 5.6.0 en mars 2000, 5.8.0 puis un long
chantier de factorisation du code qui aboutira en décembre 2007: 5.10 est une
version majeure: elle a facilité grandement la maintenance et l'intégration de
nouveaux développeurs, elle était plus rapide et elle a introduit de nombreuses
fonctionalités inspirée Perl6. Des lors, les p5p (perl5 porters, liste de
diffusion sur laquelle se retrouve les développeurs de l'interpréteur perl)
est capable de sortir une nouvelle version stable par an.

Perl est très utilisé dans du code d'infrastructure (les autotools,
texlive, git, les systèmes de paquets de debian et openbsd, ...), toutes ces
nouvelles fonctionalités qui ont permis aux bonnes pratiques d'évoluer
on du être ajoutées sans presque jamais casser la retrocompatibilité
et ne pas introduire de collision avec le code des utilisateurs du langage.
Ls dépreciations sont rares, ne concernent rien de central dans le langage
et s'étalent sur plusieurs versions avec des warnings.

Cela veut dire aussi qu'il faut ajouter de nouvelles fonctionalités avec précaution
puisque ces fonctionalités devront être supportées ad vitam aeternam et peuvent
rendre impossible des évolutions futures. Pour permettre de ménager la chèvre et le choux,
d'évoluer sans casser, d'experimenter sans garantir, perl utilise des feature gards:
des pragmas qui permettent d'activer et de désactiver finement toutes les nouvelles
fonctionalités du langage.

Pour ajouter à la richesse du langage, perl s'avère assez souple pour s'étendre en C ou en
Perl. Ainsi il existe sur le [CPAN](https://search.cpan.org) plusieurs frameworks
objet et c'est finalement [Moo](https://metacpan.org/pod/Moo) (inspiré du système OO de Perl6)
qui s'est imposé. On trouve aussi des modules pour ajouter un système de signatures
de fonctions ([Function::Parameters](https://metacpan.org/pod/Function::Parameters)),
un système de typage
([Type::Tiny](https://metacpan.org/pod/distribution/Type-Tiny/lib/Type/Tiny/Manual.pod)),
un système permettant une approche fonctionnelle de la consommation des générateurs
([Perlude](https://metacpan.org/pod/distribution/perlude/lib/Perlude.pod)) et j'en passe.

Cette profusion est une chance pour le développeur Perl mais pour les nouveaux venus, le ticket
d'entrée est d'autant plus cher que rien n'existe par défaut: il faut connaitre les bons pragmas,
les bons modules et les bonnes pratiques sans qu'elles n'apparaissent immédiatement dans
les tuto. De plus, le boilerplate s'allonge avec les années.


C'est pour ces raisons que vous apparaitre des modules qui proposent à la fois un boilerplate,
un bundle et un coding style. On peut citer [Modern::Perl](https://metacpan.org/pod/Modern::Perl),
[Perl5i](https://metacpan.org/pod/perl5i), [common::sense](https://metacpan.org/release/common-sense), [Sympatic](https://metacpan.org/pod/Sympatic).

        use Sympatic;
        # Equivalent à:
        # use strict;
        # use warnings;
        # use feature qw< unicode_strings say state >;
        # use English qw< -no_match_vars >;
        # use utf8;
        # use Function::Parameters;
        # use Moo;
        # use MooX::LvalueAttribute;

Si vous explorez ces modules, vous vous rendrez compte que le "sens commun"
n'est pas le même pour tout le monde et que Perl souffre de la
[Lisp Curse](http://www.winestockwebdesign.com/Essays/Lisp_Curse.html).
Il était temps de changer le fonctionnement par défaut de Perl et de proposer
un nouveau standard. C'est chose faite avec Perl 7 et il vous est plus
facile de comprendre la portée de l'annonce de Saywer X.

Evidement, des dents vont grincer et des (disparition de la notation indirecte,
de la syntaxe Perl4 des prototypes, ...) et une certaine inquiétude sur les
conséquences imprévues d'un changement de version (lire
"[Perl 7, not quite getting better yet](http://blogs.perl.org/users/leon_timmermans/2020/06/not-quite-getting-better-yet.html)") apparait mais il fallait que les choses évoluent
et pour tout dire: Perl méritait un changement de version depuis bien longtemps.


