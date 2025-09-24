<script lang="ts"></script>

<header>
    <div class="header-container">
        <div class="logo-container">
            <img src="/images/cw_logo.svg"/>
        </div>
        <nav></nav>
        <div class="button-container">
            <a class="cw-button--primary small" href="">Begär en offert</a>
        </div>
        <div class="hamburger-container">
            <div class="subheading text-accent">meny</div>
        </div>
    </div>
</header>

<style lang="scss">
    header {
        height: 4rem;
        background-color: var(--bg-color);
        border-bottom: 1px solid var(--border-color);
        display: grid;
        grid-template-columns: 1fr 81.125rem 1fr;
        grid-template-areas: "gutter-1 header gutter-2";

        @media (max-width: 768px) {
            border-top: 1px solid var(--border-color);
            grid-template-columns: 1fr calc(100% - 4rem) 1fr;
        }

        .header-container {
            grid-area: header;
            border-left: 1px solid var(--border-color);
            border-right: 1px solid var(--border-color);
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            align-items: center;

            @media (max-width: 768px) {
                grid-template-columns: 1fr 64px;
            }

            .logo-container {
                padding-left: 1rem;
                justify-self: flex-start;

                img {
                    max-width: 10rem;
                }

                @media (max-width: 768px) {
                    padding-left: 1rem;
                }
            }

            nav {
                justify-self: center;

                @media (max-width: 768px) {
                    display: none;
                }
            }

            .button-container {
                padding-right: 1rem;
                justify-self: flex-end;

                @media (max-width: 768px) {
                    display: none;
                }
            }

            .hamburger-container {
                display: none;
                height: 100%;
                border-left: 1px solid var(--border-color);

                @media (max-width: 768px) {
                    display: grid;
                    place-items: center;
                }
            }
        }
    }
</style>