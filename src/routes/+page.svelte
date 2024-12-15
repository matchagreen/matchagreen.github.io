<script>
    const projects = [
        {
            id: 'discord-bot',
            name: 'Discord Youtube Bot',
            description: 'This is a discord bot that will join your channel and will play the audio from the youtube link that you provided. I built this so that I could play music with my friend on Minecraft and on Stardew Valley, until we found out that Discord actually lets other people listen to whatever you are listening on Spotify :) so all this wasn\'t necessary.',
            technologies: [
                {
                    text: 'Python',
                    url: 'https://www.python.org/'
                },
                {
                    text: 'Discord.py',
                    url: 'https://discordpy.readthedocs.io/en/stable/'
                }
            ],
            links: [
                {
                    url: 'https://github.com/matchagreen/barista-bot'
                }
            ],
            image: 'discord-bot.jpg',
            alt: 'Matcha drink'
        },
        {
            id: 'portfolio',
            name: 'Portfolio Website',
            description: 'So recursive! This is a static Svelte application that uses a javascript config object to generate a lot of the elements on the page. This could have arguably been a pure Javascript, HTML, and CSS page but I wanted an excuse to try out Svelte.',
            technologies: [
                {
                    text: 'Svelte',
                    url: 'https://svelte.dev'
                },
                {
                    text: 'Sass',
                    url: 'https://sass-lang.com'
                }
            ],
            links: [
                {
                    url: 'https://github.com/matchagreen/matchagreen.github.io'
                }
            ],
            image: 'portfolio.png'
        },
        {
            id: 'connect-4',
            name: 'Connect 4',
            description: 'This is a server-client based Connect 4 game. The server provides the rules of the game, as well as an opponent to the player, while the client serves as an interface where the user can make their moves and see the status of the game. A star is shown at the bottom of the grid to indicate the last movement done for clarity.',
            technologies: [
                {
                    url: 'https://www.php.net/',
                    text: 'PHP'
                },
                {
                    url: 'https://dart.dev/',
                    text: 'Dart'
                }
            ],
            links: [
                {
                    url: 'https://github.com/matchagreen/Connect-4-Server',
                    text: 'Server'
                },
                {
                    url: 'https://github.com/matchagreen/Connect-4-Client',
                    text: 'Client'
                }
            ],
            image: 'connect-4.jpg',
            alt: 'Connect 4 game being played on a terminal'
        },
        {
            id: 'can-bus-visualizer',
            name: 'CAN Bus Visualizer',
            description: 'This is a web application written in React and Typescript. It allows an analyst to view information gathered from the CAN Bus of a vehicle. It displays the traffic gathered from the vehicle in a table, and it shows the sensors as nodes on a map (used Reactflow for the diagram). I lead the Front end team responsible for the look and feel of the application, and collaborated with the Backend team to define the API calls.',
            technologies: [
                {
                    url: 'https://react.dev/',
                    text: 'React'
                },
                {
                    url: 'https://www.typescriptlang.org/',
                    text: 'Typescript'
                }
            ],
            links: [
                {
                    url: 'https://github.com/iarivas/CS4311_CANBusVisualizer_Team_6'
                }
            ],
            image: 'can-bus-visualizer.png',
            alt: 'Screen of a website showing nodes and message data from a CAN Bus'
        },
        {
            id: 'quiz-app',
            name: 'Quiz App',
            description: 'This is a mobile multi-platform app. It obtains a list of questions from the University of Texas at El Paso\'s server. A user can then select a number of random questions to answer and receive a score and feedback at the end. It requires a user to authenticate themselves.',
            technologies: [
                {
                    url: 'https://dart.dev/',
                    text: 'Dart'
                },
                {
                    url: 'https://flutter.dev/',
                    text: 'Flutter'
                }
            ],
            links: [
                {
                    url: 'https://github.com/matchagreen/quiz_app'
                }
            ],
            image: 'quiz-app.png',
            alt: 'Screenshot of a mobile app where a user is prompted to answer questions on a quiz'
        }
    ];

    const technologies = [
        {
            name: 'Vue.js',
            link: 'https://vuejs.org',
            category: 'frontend',
            usedAtWork: true
        },
        {
            name: 'Groovy',
            link: 'https://groovy-lang.org',
            category: 'backend',
            usedAtWork: true
        },
        {
            name: 'Javascript',
            link: 'https://developer.mozilla.org/en-US/docs/Web/JavaScript',
            category: 'frontend',
            usedAtWork: true
        },
        {
            name: 'Express.js',
            link: 'https://expressjs.com',
            category: 'backend',
            usedAtWork: true
        },
        {
            name: 'Redis',
            link: 'https://redis.io',
            category: 'backend',
            usedAtWork: true
        },
        {
            name: 'Python',
            link: 'https://www.python.org',
            category: 'backend',
            usedAtWork: false
        },
        {
            name: 'FastAPI',
            link: 'https://fastapi.tiangolo.com',
            category: 'backend',
            usedAtWork: false
        },
        {
            name: 'React.js',
            link: 'https://react.dev',
            category: 'frontend',
            usedAtWork: false
        }
    ]

    const icons = [
        {
            icon: 'github.svg',
            url: 'https://github.com/matchagreen',
            alt: 'Github icon'
        },
        {
            icon: 'linkedin.svg',
            url: 'https://www.linkedin.com/in/alan-perez-520780207/',
            alt: 'Linkedin icon'
        },
        {
            icon: 'email.svg',
            url: 'mailto:alanperezse@gmail.com',
            alt: 'Email icon'
        },
    ]

    function makeBEM(className, modifiers) {
        return [
            className,
            ...Object.entries(modifiers).filter(([, apply]) =>
                apply
            ).map(([modifier]) =>
                modifier
            ).map(modifier => `${className}--${modifier}`)
        ].join(' ');
    }

    $: technologiesUsedAtWork = technologies.filter(technology => technology.usedAtWork);
    $: technologiesNotUsedAtWork = technologies.filter(technology => !technology.usedAtWork);
</script>

<div class='app'>
    <div class='main'>
        <div class='main__me'>
            <div class='main__me__content'>
                <div class='main__me__content__card'>
                    <div class='main__me__content__card__title' id='about-me'>About Me</div>
                    <p>
                        My name is Alan Perez, and I am a Software Engineer at Bloomberg. In my day to day, I work with fullstack web development technologies such as
                        {#each technologiesUsedAtWork as technology, index }
                        { index > 0 ? index < technologiesUsedAtWork.length - 1 ? ', ' : ' and ' : '' }
                        <a href={technology.link} target='_blank'>{ technology.name}</a>
                    {/each}
                    </p>
                    <p>I am also familiar with other technologies such as
                    {#each technologiesNotUsedAtWork as technology, idx}
                        <a href={ technology.link }>
                            { technology.name }
                        </a>{
                            technologiesNotUsedAtWork.length === idx + 1 ? '' :
                            technologiesNotUsedAtWork.length === idx + 2 ? ' and ' : ', '
                        }
                    {/each}
                    , but I am always open to learning new technologies.</p>
                    <p>I would like to contribute to companies and projects that promote welfare, or otherwise make a positive wholesome impact.</p>
                    <p>Feel free to contact me if you are interested in collaborating or chatting.</p>
                    <div class='main__me__content__card__icons'>
                        {#each icons as {icon, url, alt}}
                            <a href={ url } target='_blank' class='main__me__content__card__icons__icon'>
                                <img
                                    class='main__me__content__card__icons__icon__image'
                                    src={ icon }
                                    alt={ alt }
                                />
                            </a>
                        {/each}
                    </div>
                </div>
            </div>
        </div>
        <div class='main__portfolio'>
            <div class='main__portfolio__title'>Portfolio</div>
            {#each projects as project, index}
                <div class='main__portfolio__project'>
                    <div class='main__portfolio__project__title'>
                        [ { project.name } ]
                    </div>
                    <div class='main__portfolio__project__content'>
                        <img
                            class='main__portfolio__project__content__image'
                            src={ project.image }
                            alt={ project.alt }
                        />
                        <div class='main__portfolio__project__content__description'>
                            <div>{ project.description }</div>
                            {#if project.links?.length}
                                <div class='main__portfolio__project__content__description__links' >
                                    <span>Links:</span>
                                    {#each project.links as link, index }
                                        {#if index > 0}
                                            <span>, </span>
                                        {/if}
                                        <a href={link.url} target='_blank'>{link.text ?? 'Repository'}</a>
                                    {/each}
                                </div>
                            {/if}
                            {#if project.technologies?.length}
                                <div class='main__portfolio__project__content__description__technologies' >
                                    <span>Technologies:</span>
                                    {#each project.technologies as technology, index }
                                        {#if index > 0}
                                            <span>, </span>
                                        {/if}
                                        <a href={technology.url} target='_blank'>{technology.text}</a>
                                    {/each}
                                </div>
                            {/if}
                        </div>
                    </div>
                    {#if index < projects.length - 1}
                        <div class='main__portfolio__project__divider'></div>
                    {/if}
                </div>
            {/each}
        </div>

        <div class='main__disclaimer'>
            Background image provided by Unsplash. Made with &lt;3
        </div>
    </div>
</div>


<style lang='scss'>
a {
    color: #e4894b;
    text-decoration: none;
}

.app {
    color: rgb(237, 234, 226);
    background-color: #1c1c1f;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 16px;
    line-height: 24px;
    min-height: max(100vh, 400px);
}

.main {
    min-width: 400px;
    background-image: url('iceland2.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    background-position: center;

    &__me {
        padding: 40px 60px;
        min-height: max(100vh, 400px);
        box-sizing: border-box;

        &__content {
            display: flex;
            justify-content: center;

            &__card {
                max-width: 900px;
                background-color: #1c1c1fcc;
                padding: 0 30px 30px;
                border-radius: 5px;

                &__title {
                    text-align: center;
                    font-size: 38px;
                    line-height: 40px;
                    padding: 21px 0 21px;
                }

                &__icons {
                    &__icon {
                        margin-right: 20px; // TODO: Don't apply this to the last element

                        &__image {
                            height: 30px;
                            width: 30px;
                            background-repeat: no-repeat;
                            background-size: cover; 
                        }
                    }
                }
            }
        }
    }

    &__portfolio {
        padding: 0 40px;
        background-color: #1c1c1f;

        display: flex;
        flex-direction: column;
        flex-grow: 1;

        &__title {
            font-size: 38px;
            line-height: 40px;
            padding: 21px 0;
            text-align: center;
        }

        &__project {
            padding: 20px 0 0;
            display: flex;
            flex-direction: column;

            &__title {
                font-size: 24px;
                line-height: 28px;
                padding: 21px 0;
                text-align: center;
            }

            &__content {
                padding-top: 10px;
                display: flex;
                min-height: 500px;

                @media screen and (max-width: 600px) {
                    flex-direction: column;
                }

                &__description {
                    padding-left: 50px;

                    @media screen and (max-width: 600px) {
                        padding: 30px 0;

                    }

                    &__links {
                        margin-top: 20px;
                    }
                }

                &__image {
                    min-height: 300px;
                    max-height: 300px;
                    min-width: 400px;
                    max-width: 400px;
                    object-fit: contain;
                }
            }

            &__divider {
                height: 1px;
                width: 70%;
                align-self: center;
                background-color: rgba(237, 234, 226, 0.417);
            }
        }
    }

    &__disclaimer {
        font-size: 11px;
        color: rgba(237, 234, 226, 0.417);
        padding-left: 5px;
        background-color: black;
    }
}
</style>

