<script lang="ts"></script>

<footer>
    <div class="footer-wrapper">
        <div class="footer-container">

        </div>
        <div class="stripe-container monochrome-striped-background">
        </div>
        <div class="bottom-container">
            <p class="subheading">&copy; Createweb 2025</p>
            <p class="subheading email">hej@createweb.se</p>
            <p class="subheading">Integritetspolicy</p>
        </div>
    </div>
</footer>

<style lang="scss">
    footer {
        height: fit-content;
        background-color: var(--bg-color);
        border-top: 1px solid var(--border-color);
        display: grid;
        grid-template-columns: 1fr 81.125rem 1fr;
        grid-template-areas: "gutter-1 footer gutter-2";

        @media (max-width: 768px) {
            grid-template-columns: 1fr calc(100% - 4rem) 1fr;
        }

        .footer-wrapper {
            grid-area: footer;
            border-left: 1px solid var(--border-color);
            border-right: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;

            .footer-container {
                height: 256px;
            }

            .stripe-container {
                border-top: 1px solid var(--border-color);
                height: 3rem;
            }

            .bottom-container {
                border-top: 1px solid var(--border-color);
                height: 3rem;
                display: flex;
                justify-content: space-between;
                align-items: center;
                padding: 0 1rem;

                @media (max-width: 768px) {
                    .email {
                        display: none;
                    }
                }
            }

        }
    }
</style>